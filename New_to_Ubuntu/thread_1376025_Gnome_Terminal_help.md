---
title: "Gnome Terminal help"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Rperalta95 on 2010-01-08
Okay. I open open the terminal the usual way. It loads all of a sudden with these words pop up here's a copy of what it says-

key3.db
tar: signons*.txt: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
--2010-01-08 17:23:40--  [http://shiftytransfer.x10hosting.com/index.php](http://shiftytransfer.x10hosting.com/index.php)
Resolving shiftytransfer.x10hosting.com... 74.63.233.3
Connecting to shiftytransfer.x10hosting.com|74.63.233.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 0 [text/html]
Saving to: `index.php'

    [ <=>                                                                                                                    ] 0           --.-K/s   in 0s

2010-01-08 17:23:41 (0.00 B/s) - `index.php' saved [0/0]

bash: warning: here-document at line 10 delimited by end-of-file (wanted `_EOF_')
[EMAIL="peralta@peralta-desktop:%7E/.mozill"]peralta@peralta-desktop:~/.mozill[/EMAIL]a$

Any ideas?

Edit:
No I didn't open it with a script. I just opened it with the icon in the menu.

---

### Post by J V on 2010-01-08
its running tar, wget, and possibly other programs on startup... opened it with a script?

---

### Post by garfilth on 2010-01-11
im getting the same on kubuntu 9.10. 

look in your /home/YOURUSERNAME/.mozilla folder and you will see some files, called key3.db and a tar file called Unlucky.

No idea what they are. if you open key3.db with a text editor its just nonsence. 

i think it might be malware of some sort ( might be wrong ). as i uninstalled firefox through synaptic and use firefox from their website. i delete the .moziila folder, reboot and its there again.

anyone with else with this problem, as a google search finds nothing. i even went to the website [http://shiftytransfer.x10hosting.com/index.php](http://shiftytransfer.x10hosting.com/index.php) and nothing happens. x10hosting is a web hosting site.

any ideas/

thanks in advance

---

### Post by Darce on 2010-01-11
This guy is having the same problem

[http://ubuntuforums.org/showthread.php?p=8639951#post8639951](http://ubuntuforums.org/showthread.php?p=8639951#post8639951)

---

### Post by Rperalta95 on 2010-01-26
I just gave up and reinstalled Ubuntu all over. It didn't take long and it worked.:wink:

---

