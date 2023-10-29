# MetaCrafter
This is a sample Solidity smart contract that aims to explain the core ideas behind Solidity. Three state variables are included in it: myTokenName, myTokenSymbol, and myTokenSupply. Additionally, it uses a mapping named "userTokenBalances" (Address => uint) to link addresses to corresponding token balances. The two functions "acquireTokens" and "removeTokens," which carry out the tasks suggested by their names, are included in the contract. acquireTokens adds a predetermined amount to the balance of the address that initiates the function, increasing the overall token supply. The removeTokens function lowers both the caller's token balance and the total supply after determining whether the caller has enough tokens.


# Starting Out:

You can use Remix, an online Solidity Integrated Development Environment (IDE), to run this program. Take these actions:
Visit https://remix.ethereum.org/.
Create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension, for example, "Test.sol."
Copy and paste the provided code into the file.
Contract Code:
```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyTokenContract {

    // Public variables for the unique token's name, symbol, and total supply
    string public myTokenName = "MyUniqueToken";
    string public myTokenSymbol = "MUT";
    uint public myTokenTotalSupply = 0;

    // Mapping to track account balances
    mapping(address => uint) public userTokenBalances;

    // Mint function to increase the total supply and user's balance
    function acquireTokens(address _user, uint _amount) public {
        myTokenTotalSupply += _amount;
        userTokenBalances[_user] += _amount;
    }

    // Burn function to decrease total supply and user's balance
    function removeTokens(address _user, uint _amount) public {
        // Checks if the user has enough tokens to burn
        if (userTokenBalances[_user] >= _amount) {
            myTokenTotalSupply -= _amount;
            userTokenBalances[_user] -= _amount;
        }
    }
}
```

Make sure the "Compiler" option is set to "0.8.18" (or another compatible version) under the "Solidity Compiler" tab in the left-hand sidebar in order to build the code. Select "Compile Test.sol" from the menu.



Once the contract has been compiled, you may deploy it by selecting the "MyTokenContract" contract from the dropdown menu on the "Deploy & Run Transactions" tab in the sidebar, then clicking the "Deploy" button.



After the contract is deployed, you can use the Remix interface to call the "acquireTokens" and "removeTokens" functions to communicate with it. Ensure that the compiler option is configured to 0.8.18 in order to prevent version dependency issues.

# Writer:
[Piyush]

# Permission:



The MIT License governs the use of this project. See the LICENSE.md file for further information.
