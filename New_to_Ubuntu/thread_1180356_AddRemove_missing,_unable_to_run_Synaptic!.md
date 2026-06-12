---
title: "Add/Remove missing, unable to run Synaptic!"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Tholley on 2009-06-06
I am running 9.04 and have been messing with different media players all day, but now when I went to add VLC, I notice my Add/Remove was missing, so then I went to Synaptic 
Package Manager, and typed in my password, I get this message... 

Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I rebooted, thinking it was a glitch, but still the same. 

What in the world could I have done to mess this up?

---

### Post by HereInOz on 2009-06-06
Can you try installing vlc from the command line

sudo apt-get install vlc

This will let you know whether it is Synaptic which is broken, or whether you are unable to run anything with root privilidges.

---

### Post by Tholley on 2009-06-06
Nope... this is what I got...

terrell@terrell-bedroom:~$ sudo apt-get install vlc
[sudo] password for terrell: 
terrell is not in the sudoers file.  This incident will be reported.
terrell@terrell-bedroom:~$

---

### Post by oldos2er on 2009-06-06
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Tholley on 2009-06-06
Thanks Ann!
I printed that out and will give it a shot.

---

### Post by HereInOz on 2009-06-06
It looks like you have somehow removed your ability to administer the system.  

Clearly, someone must have the ability of administrator, at least through sudo, but if you now have no-one who has administrator capability, you could be in a little bit of strife.

It is always a good idea to set up a second user who can administer the system, just in case something like this happens.

I hope the tutorial to which Ann has pointed you will help.

---

### Post by Tholley on 2009-06-06
Ok it worked! Not at first, but the second try doing the "adduser terrell admin" worked. It _seems_ everything is back to normal. I was able to install VLC from Add/Remove  and opening Synaptic seemed all good too.

Thanks guys!

I have no idea how I screwed it up in the first place.

---

