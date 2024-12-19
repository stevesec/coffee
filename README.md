# Coffee

This script automates sending key presses using a combination of Batch and JScript. It repeatedly sends the `ENTER` key after a specified delay, which can be adjusted to suit your requirements.

## Script Explanation

### Batch Section
```batch
@if (@CodeSection == @Batch) @then

@echo off
    set SendKeys=CScript //nologo //E:JScript "%~F0"
    cls
    color 0a
    :loop
        %SendKeys% "{ENTER}"
        timeout /t 30 /nobreak >nul
    goto :loop

@end
```
- **`set SendKeys`**: Defines a variable that runs the embedded JScript using `CScript`.
- **`timeout /t 30 /nobreak >nul`**: Waits for 30 seconds before sending the next key press. This value can be adjusted to change the delay.
- **`goto :loop`**: Ensures the script runs indefinitely in a loop.

### JScript Section
```javascript
var WshShell = WScript.CreateObject("WScript.Shell");
WshShell.SendKeys(WScript.Arguments(0));
```
- **`WScript.CreateObject("WScript.Shell")`**: Creates a Shell object to send key inputs.
- **`SendKeys`**: Sends the specified key (in this case, `ENTER`).

## Usage
1. Save the script with a `.bat` extension (e.g., `SendKeysScript.bat`).
2. Run the script in a command prompt.
3. The script will repeatedly send the `ENTER` key every 30 seconds by default.

## Customization
- **Adjusting the Timeout**: Modify the value in the `timeout` command:
  ```batch
  timeout /t <desired_seconds> /nobreak >nul
  ```
  Replace `<desired_seconds>` with the number of seconds you want between key presses.
- **Changing the Key**: Replace `"{ENTER}"` in the Batch section with the desired key sequence (e.g., `"a"` to send the `A` key).

## Notes
- Ensure the script runs in an environment that supports both Batch and JScript.
- Use responsibly, as it simulates repeated key presses which might interfere with other applications.

## Example
To send the `ENTER` key every 10 seconds:
```batch
        timeout /t 10 /nobreak >nul
```
Save the file and run it to observe the modified behavior.
