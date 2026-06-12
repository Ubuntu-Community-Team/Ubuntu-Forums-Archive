---
title: "Pigdin not working with MSN addresses"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by freeediver on 2009-12-08
Any idea what has changed and how to fix it?

---

### Post by llawwehttam on 2009-12-08
Quite recently (as in the last week) Microsoft sent out an update for MSN which means that it gets its details about the user from the msn space profile thingy. Because of this it is proving difficult to set up msn accounts with alternative clients and even if you have before you might be unable to change your nickname without creating an MSN profile or doing it from a windows box. 

Personally as a messenger I use Emesene or aMSN. I don't know if there is a fix for pidgin but Emesene seems to be working fine for me.

---

### Post by ubhi on 2009-12-08
u can do it by alternate method...

if u know already bout meebo, then its okay otherwise u can choose anything from yahoo, msn, google etc

[http://www.meebo.com/](http://www.meebo.com/)

---

### Post by fhrosa on 2009-12-08
Same problem here. It shows a message box "Our protocol is not supported by the server".

---

### Post by Super TWiT on 2009-12-08
Me too. Noticed it this afternoon when I came home.

---

### Post by slumbergod on 2009-12-08
maybe the msn-pecan plugin for pidgin will work for you? I haven't noted any problems with pidgin and msn but then I am not using the default msn setup.

---

### Post by fhrosa on 2009-12-10
I've looked into it ([http://code.google.com/p/msn-pecan/](http://code.google.com/p/msn-pecan/)) but it seems non-trivial getting it to work on Ubuntu LTS (8.04). No package on the repositories, the .deb provided on the website is for another arch, and trying to compile from source fails:

mentus@mentecaptoHP:~/tmp/msn-pecan-0.1.0-rc1$ make
[SHLIB] libmsn-pecan.so
switchboard.o: In function `datacast_msg':
/home/mentus/tmp/msn-pecan-0.1.0-rc1/switchboard.c:1424: undefined reference to `purple_prpl_got_attention_in_chat'
/home/mentus/tmp/msn-pecan-0.1.0-rc1/switchboard.c:1426: undefined reference to `purple_prpl_got_attention'
collect2: ld returned 1 exit status
make: *** [libmsn-pecan.so] Error 1

So stuck without msn for the moment being...

---

### Post by sliketymo on 2009-12-10
I use pidgin on both Ubuntu,and windows and have not had any problems with it.You may try running a quick update and see if that helps.I have noticed that msn has it's moments not related to pidgin itself.

---

### Post by fhrosa on 2009-12-12
Which version of Ubuntu and Pidgin are you running?

Here it's LTS 8.04 and Pidgin 2.4.1.

---

### Post by rolnics on 2009-12-12
I'm not noticing any problems, I'm using 8.04.3 and Pidgin 2.6.3, just got notification about new emails.

---

### Post by fhrosa on 2009-12-13
> Ok, great. I've just checked and I'm running Ubuntu 8.04.3 LTS too. But if when I do a apt-get install pidgin it says it's already on the most current version (2.4.1). Do you remember how do you managed to install Pidgin 2.6.3?

Problem solved. Just adding the sources for the last releases of pidgin, as explained here [http://www.ubuntugeek.com/install-pidgin-2-6-0-in-ubuntu.html](http://www.ubuntugeek.com/install-pidgin-2-6-0-in-ubuntu.html) , enabled me to upgrade to pidgin 2.6.4, as well as compiling the pecan plug in successfully. 

Thank you!

---

### Post by freeediver on 2009-12-13
yep updating was the issue. I assumed that auto update would work
with Pigdin, not. I just installed the most current version and it is telling me that it will now auto update.
Problem solved

---

