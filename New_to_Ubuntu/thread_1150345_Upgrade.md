---
title: "Upgrade"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-05-06
(SOLVED)Thought I had a win when I upgraded to Jaunty. This certainly fixed my cd/dvd drive problem. But now I have another problem. When I go to Update Manager I receive a message saying that I can do a Partial Upgrade but when I click on "Partial Upgrade" nothing happens.
Can anyone help with this problem?

---

### Post by drs305 on 2009-05-06
It's possible that your server doesn't currently have a package available for some reason or a server itself is unavailable. You could try again later. 

If this is a persistent problem post the error message contents and we can see where the problem really is. For troubleshooting, run these from the command line:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Sef on 2009-05-06
> If this is a persistent problem post the error message contents and we can see where the problem really is. For troubleshooting, run these from the command line:
 	Code:
 	sudo apt-get update && sudo apt-get upgrade 
 		                   		  		  		 		 			

If you use those, just copy and paste.

Also **back up **your **data** before upgrading.  There are not 100% guarantees that all will go well.

---

### Post by bigal1932flying on 2009-05-06
Ran that command and 52 updates were downloaded and installed. After that Update Manager still came up with the need to do a Partial Upgrade but this time it ran through without a problem.
All seems to be well now THANKS a ZILLION.

---

