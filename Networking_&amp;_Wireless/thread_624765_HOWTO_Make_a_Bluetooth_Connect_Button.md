---
title: "HOWTO: Make a Bluetooth Connect Button"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by matthew.lns1 on 2007-11-27
This is a tutorial of how to put a button on your desktop that will connect a Bluetooth device. 
The steps are as fallows:

1. Open Text Editor from Applications>Accessories>Text Editor

2. Cut and paste this into the new file:
```
hidd --search
```

3. Save file as "Bluetooth_Search.sh" or whatever you want. It just has to end with ".sh"

4. Right click your desktop.

5. Click the "Create Launcher..." option.

6. Put "Bluetooth Connect Button" in the name field or whatever makes sence to you. 

7.Click "Browse..." and navigate to the place you saved your file earlier.

8. Double click on the file.

9. The "Command:" box should now be full of text. Navigate to the very front of all the text and type this:
```
gksu 
```

10. You can't see the space I made there but make sure you add a space between the "gksu" and the rest of the text.

11.  Click "OK"

12. Open Text Editor again.

13. Click and drag the new icon you have on your desktop into the Text Editor window.

14. You should see a line that says:
```
Terminal=false
```

15.Get rid of the false and put "true" in it's place.

Your Done!

---

