---
title: "SSH not working anymore, unsupported key algorithm in certificate: 1.2.840.10045.2.1"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by adriaan1 on 2011-02-25
So I was using SSH as happy as ever, when suddenly it was not working anymore. I checked the modem port forwarding and generated a new keypair, but no luck. In the auth.log it says

>>
Feb 25 17:58:30 beefcake-laptop-ubuntu gnome-keyring-daemon[1446]: unsupported key algorithm in certificate: 1.2.840.10045.2.1
>>

I have the feeling that this problem occured after Ubuntu installed some updates. I am using Ubuntu version 10.10.

I have googled the error but do not seem to get any useful solution. 

I do not know how I should solve this problem :(. Can anybody help me out? Would be great ;)!

---

### Post by CharlesA on 2011-02-25
Found this: 
[http://linuxindetails.wordpress.com/2009/12/30/gnome-keyring-daemon-unsupported-key-algorithm-in-certificate-1-2-840-10045-2-1/](http://linuxindetails.wordpress.com/2009/12/30/gnome-keyring-daemon-unsupported-key-algorithm-in-certificate-1-2-840-10045-2-1/)

---

### Post by adriaan1 on 2011-03-02
I installed the package libpam-unix2 (and with this I also needed to mandatorily install libxcrypt1), but I still get the exact same error :(....

---

### Post by CharlesA on 2011-03-02
It kinda sounds like the keyring is messing something up.

I haven't been able to find any info about how to disable the keyring for ssh.

Only thing I found was this: [http://ubuntuforums.org/showthread.php?t=796410](http://ubuntuforums.org/showthread.php?t=796410)

---

### Post by adriaan1 on 2011-03-04
So as suggested, I tried some things in the System->Prefrences->Startup applications. Unfortunately without any luck. I keep getting the same errors.

I unchecked 'Certificate and Key Storage', 'Remote Desktop', 'Secret Storage Service' and 'SSH Key Agent' simultaneously. Didn't help.

At [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/610982](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/610982), they have a similar discussion, but I can not make enough out of the discussion to solve the problem. Perhaps someone else understands it better?

But indeed, it could very well be that the problem occured for the first time since I upgraded my 10.04 to 10.10. At work I have 10.04, at home 10.10. SSH-ing from home to work is not a problem at all, but the other way around is giving the 'connection refused' :(.

---

