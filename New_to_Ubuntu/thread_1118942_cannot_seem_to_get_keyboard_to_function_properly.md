---
title: "cannot seem to get keyboard to function properly"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by malahavock on 2009-04-07
Can anyone tell me how to get my extra keys to function properly. I have a logictech Ex 110. I have gone through the keytouch process I even made my own ex 110 keyboard layout. but it doesn't work. my help key launches word my f2 key logs me out of my system. I have no idea why it would do that. and I am kinda at a loss now after trying keytouch 10 times to make sure I had applied everything correctly which I think I did but apparently something is not right. 


ubuntu 8.10 x64 

thanks!!

I was worng it isn't my f2 it's the f3 which is supposed to open the office spreadsheet. that logs me out.

---

### Post by malahavock on 2009-04-07
Does anyone know how do disable the F3 function from the keymap? maybe am I on the right path? Does anyone know?


OK I have figured out that I am not being logged out per se it is running my screensaver. so Now I can't find anywhere to tell it to stop. screensaver settings has nothing about a hotkey for the screensaver I REALLY need this to go away. Any one with any ideas out there????

---

### Post by Penguin Guy on 2009-04-14
**Setting Your Keyboard Model Correctly**
Goto: System -> Preferences -> Keyboard
Click on the 'Layout' tab
Now set your keyboard model to whatever model it actually is.


**Resetting Your Keyboard Shortcuts**
```
useradd temp
```
It should ask you for a password: Type a random one in.

```
sudo cp -R /home/temp/.gconf/desktop/gnome/peripherals/keyboard ~/.gconf/desktop/gnome/peripherals/keyboard
```
It should ask you for a password: Type *your* password in.

```
sudo userdel -r temp
```

Good luck!

---

