---
title: "Graphical User Switcher Error"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-04-12
I have just removed the password for my guest account with [COLOR="Green"]passwd -d guest[/COLOR]. Then I clicked on 'guest' in the user menu to see if the password removal had worked and it brought up the error message below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=109578&stc=1&d=1252064989[/IMG]

Apparently the error message is meaningless, try to switch users again and it should work.

---

### Post by lavinog on 2009-04-12
I take it that you are trying to remove the Guest session from the list?
You could try
```
sudo apt-get remove gdm-guest-session
```

---

### Post by Penguin Guy on 2009-04-12
Sorry, I did not make myself clear. I was trying to remove the password from the guest account; when I went to test it it brought up an error.

---

### Post by Denestria on 2009-04-12
If you want a no password guest login try

[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)

---

### Post by Penguin Guy on 2009-04-13
Thanks, but I am still wondering what the error means.

---

### Post by louieb on 2009-04-13
The error means the 2nd X session for the user did not start. 
I get that error every now and then both in v8.04 Hardy and v8.10 Intrepid. I just click on the user again and it works. 

It doesn't bother me enough to check but you might try [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") and see what others a doing when they get that error message.

---

### Post by Penguin Guy on 2009-04-13
Thanks, I was just quite worried that my GUI might stop working; all appears fine after rebooting.

---

