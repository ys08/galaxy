
# Debugging Galaxy

## Debugging Galaxy in VS Code 

The following instructions assume that you have cloned your Galaxy fork into the `~/galaxy` directory and have created a VS Code workspace per instructions [here](./debugging_tests.md)

1. Add the following code snippet to `~/galaxy/.vscode/launch.json` (create the file if it does not already exist)
    ``` 
    {
        "version": "0.2.0",
        "configurations": [
            {
                "name": "Python: Current File (Integrated Terminal)",
                "type": "python",
                "request": "launch",
                "program": "${file}",
                "console": "integratedTerminal"
            },
            {
                "name": "Galaxy debug",
                "type": "python",
                "request": "launch",
                "program": "${workspaceFolder}/scripts/paster.py",
                "args": [
                    "serve",
                    "config/galaxy_vscode.ini",
                    "--log-file",
                    "galaxy.log",
                ],
            }
        ]
    }

    ```
2. Re-start VS Code
3. Add a breakpoint somewhere in your code
4. Select Run and Debug on Activity Bar, on the far left hand side. In the RUN AND DEBUG drop down, select Galaxy debug (galaxy), and click the Start Debugging button (green arrow)
5. Galaxy should stop right on the break point you added.
6. Enjoy your debugging session :-)
