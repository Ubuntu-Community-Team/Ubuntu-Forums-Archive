---
title: "password not recognised, can't log in"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by quercusrobur on 2009-11-18
Further problems, earlier I was having problems with File Manager, found a piece of advice on these forums which suggested deleting and reinstalling Nautilus which I did. I then tried to restart my laptop but found my password was no longer being recognised.

Then tried to restart in recovery mode which requested and seemed to recognse my username and passwords but hasn't gotten beyond this. Is there a command I need to be entering to continue the start up process???

---

### Post by ukripper on 2009-11-18
how did you remove and reinstalled nautilus?

---

### Post by ranch hand on 2009-11-18
If you are getting to a text login then you need to log in with user name and password.

You will get a prompt again and type;
```

startx

```
If everything is cool your desktop will open.

---

### Post by Cheesemill on 2009-11-18
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by quercusrobur on 2009-11-18
ranch hand - typed in startx, now I have a blank screen apart from the cursor arrow


ukripper - not sure of the code I used, but I copied and pasted it into the terminal as per the instructions, I've been looking for the post I followed but so far no luck....

---

### Post by quercusrobur on 2009-11-18
I'm guesing that I managed to delete nautilus but didn't reinstall it properly????

---

### Post by ukripper on 2009-11-18
while re-installing nautilus if you have missed some dependencies then this command will resolve it for you:
```
sudo aptitude -y install ubuntu-desktop
```

---

### Post by quercusrobur on 2009-11-18
thanks UK Ripper - problem at the moment though is that I can't start my laptop at all (and I think this old one I'm using at the moment is about to die a death too!!!), or at least i can't get it past the above described black screen and curser arrow. Is there any way I can open the terminal from keystrokes?

---

### Post by ukripper on 2009-11-18
can you normally boot into your ubuntu installtion and when it reaches your login screen press CTRL + ALT + F1. put your username and password there and run the command i gave you above.

---

### Post by quercusrobur on 2009-11-18
Thanks UKripper, I'm back in with a functioning desktop and back on my own laptop now, however I still have the original problem of the file manager seeming to crash or freeze whenever I click on any desktop icons. I've now found the page I was refering to earlier, it's [http://ubuntuforums.org/showthread.php?t=1327103&highlight=nautilus&page=2](http://ubuntuforums.org/showthread.php?t=1327103&highlight=nautilus&page=2)

---

### Post by quercusrobur on 2009-11-18
also typed 'nautilus' into a terminal and got this output;

graham@graham-laptop:~$ nautilus

(nautilus:2473): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by quercusrobur on 2009-11-18
Finally worked out that a corrupt file on the desktop was causing the problem, but couldn't delete it as everytime I went anywhere near it Nautilus would freeze - eventually dealt with it by installing Thunar and using that to delete it - everything seems to be working fine now!!

Thanks for all the help and advice!! Much appreciated!!

---

