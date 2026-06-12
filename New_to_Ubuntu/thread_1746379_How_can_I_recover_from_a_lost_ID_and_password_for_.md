---
title: "How can I recover from a lost ID and password for Ubuntu 9.04"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by jbosw on 2011-05-01
Hi Forum!
 
[FONT=Calibri][SIZE=3]I am a new LINUX user, having inherited a PC with some data and work on it I need from a guy who left a project two years ago and can’t be located.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]So my questions are essentially (1) can I recover access from this, or (2) can I download the most recent version of Ubuntu and lay it on top of what I have and still preserve the data and user developed software that is on there, or (3) both, my choice?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have five screen shots that show as far as I have been able to go ….[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3](1)[/SIZE][/FONT]    [/FONT][FONT=Calibri][SIZE=3]The first; of the Ubuntu sign-on screen.  The version is 9.04.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3](2)[/SIZE][/FONT]    [/FONT][FONT=Calibri][SIZE=3]The second; shows me selecting the recovery mode, after hitting ESC during boot-up[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3](3)[/SIZE][/FONT]    [/FONT][FONT=Calibri][SIZE=3]The third; shows me getting to the Recovery Menu.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3](4)[/SIZE][/FONT]    [/FONT][FONT=Calibri][SIZE=3]The fourth; shows what happens if I select the “Update grub boot loader” from the menu.  It whizzes by much too fast and goes straight back to the Recover Menu.  No chance to work with a prompt.  I had to freeze the scrolling to take this screen shot.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3](5)[/SIZE][/FONT]    [/FONT][FONT=Calibri][SIZE=3]The fifth; shows what happens if I select “Drop to root shell prompt”.  I don’t get to a  prompt, but get stuck in a control/D loop.[/SIZE][/FONT]
 
[If you acutally need to see the screen shots to be helpful, how do I post them or get them to you?]
 
[FONT=Calibri][SIZE=3]Thanks much.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Yours,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Joe [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by josephmills on 2011-05-01
hi joe 
If you forgot you password for your ubuntu system you can recover using the following steps
Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel &#8230;&#8230;&#8230;, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot
source [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by jbosw on 2011-05-02
Hi Joe!
Thanks for your quick reply last night.  I was also missing my user IDs, so I needed to use "ls /home" to find out what they were - and reset all of them.  So your feedback, in conjunction with what I found at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) did the trick.  Thanks again.
Yours,
Joe

---

