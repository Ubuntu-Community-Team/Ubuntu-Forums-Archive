---
title: "mount in Ubuntu eee"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by fcf on 2008-12-17
I'm absolutely beginning to be an absolute beginner. I'd like to mount a sd disk and a usb key into my EEE 901 and  it tells me I have to be a superuser to do it.

Could anybody very slowly explain to an old man finally fed up with MS how to do it?

I'm afraid the style has to be:

1-Turn on computer
2-introduce key
...

My eternal gratitude and, remember, it's Christmas time!

---

### Post by indytim on 2008-12-17
If the device is appearing on your desktop when you insert the device into the usb port or the reader is inserted into the usb port, then try "right clicking" on the icon.  Should see an option like "mount".  The specifics vary by distro and version, but the concept should be pretty universal.

And welcome to the Linux ops.

IndyTim

---

### Post by fcf on 2008-12-17
Thank u very much. I tried this, but nothing happens.As soon as I put the device in the computer, the icon appears, with a message:

"Cannot mount volume. You have to have superuser rights to do it"

The right click doesn't work on the icon and I'm stuck.

Thks

---

### Post by theozzlives on 2008-12-17
are you using your Admin acct (the acct you setup during install)?

If so, try hitting alt+F2 and type: gksudo natilus, then mount

---

### Post by fcf on 2008-12-17
Yes, quite so.

---

### Post by minsf on 2008-12-17
> **theozzlives said:**
> 
If so, try hitting alt+F2 and type: gksudo natilus, then mount

should be nautilus of course :)

---

### Post by fcf on 2008-12-17
When I typed gksudo nautilus, it reinstalled "dropbox", last program I'd installed. Now I have 2 dropboxes and still no mounting! by the way, can anyone tell me how I get rid of the second dropbox?

Thx

---

### Post by minsf on 2008-12-17
do you have a special built in drive for the sd, or do you connect the sd card through the usb?

in the meantime, let me focus on the usb key; first, i would like to see some information on your usb hardware. here's how to get it:

A) get a terminal window. this first step is important, since most of the things we will suggest here will involve typing some commands in a terminal window. here's how you get it:
1) in the upper left corner of your screen you should see the ubuntu logo. click on the "Applications" next to it (it's like the start menu in the bottom left corner in Win).
2) in the drop-down menu, choose "Accessories" (this is probably the first option).
3) in the next menu choose "Terminal" (this is probably the 7th option).
4) a window will open, and you should see something like "you@your-laptop$".
5) the idea is that you type commands to the right of the $ sign. you hit enter when you finish typing, and then you will get some results and another $ sign (prompt) so that you can type in your next command.

B) for any command that people suggest here, you can view its help file by typing "man command" to the right of the $ sign and hitting enter. for instance, i am going to suggest that you use the lsusb command, and if you dont trust me (who knows, maybe i give you a malicious command), you can view the help file of this command by typing "man lsusb" (without the quotes) to the right of the $ prompt and pressing enter. by the way, you can scroll the help file with the up and down arrows and you can exit it by pressing "q" (without the quotes) which will take you back to the lovely $ prompt.

C) in the terminal window, type "lsusb -v|less" (without the quotes) to the right of the $ prompt and press enter. you can scroll the output again with the up and down arrows, and exit with "q".

D) i want you to post here the output of this command. note: to cut it from the terminal screen, you will use the ctrl+SHIFT+c, rather than the conventional ctrl+c. to paste it in the browser, the conventional ctrl+v will probably work.

when we have this info, we will probably be able to give you more advice. also dont forget to answer my first question: do you have a built in sd drive?

---

