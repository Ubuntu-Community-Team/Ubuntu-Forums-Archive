---
title: "How to disable root in karmic?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by LearningPerson on 2010-04-11
Can't get into my Ubuntu hard drive and one thing I thought might help was to give root a password.  Now I am denied permission.  

I have found the following:

sudo passwd -l root

but the command line keeps asking me for my password and won't accept just "Enter".

Please help.  Thanks.

---

### Post by spcwingo on 2010-04-11
That command should work if you reboot into "recovery mode" and drop to a root shell.

---

### Post by Calash on 2010-04-11
Turning on Root is never a good idea unless you specifically have a need to do it.  In all cases these are advanced needs often due to hardware access or code issues.

That aside, why do you think it will help?  What problems are you seeing with your hard drive?

---

### Post by spcwingo on 2010-04-11
> **Calash said:**
> Turning on Root is never a good idea unless you specifically have a need to do it.  In all cases these are advanced needs often due to hardware access or code issues.

That aside, why do you think it will help?  What problems are you seeing with your hard drive?

I think you misunderstood.  He's trying to re-lock the root account, not unlock.

---

### Post by wojox on 2010-04-11
This is about all the root help you can receive here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> That command should work if you reboot into "recovery mode" and drop to a root shell.

Do you mean at the    sh:grub:    command line

or the  <username>: ~#        command line?

I can get back to grub by typing "e" at my grub menu.....which still comes up altho it takes me only to the rotating circle as I have a Gconfig problem.

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> I think you misunderstood.  He's trying to re-lock the root account, not unlock.


Actually it's a she attempting not to have to sign in as Root - I DO want to disable Root.

Thanks.

---

### Post by LearningPerson on 2010-04-11
> **Calash said:**
> Turning on Root is never a good idea unless you specifically have a need to do it.  In all cases these are advanced needs often due to hardware access or code issues.

That aside, why do you think it will help?  What problems are you seeing with your hard drive?


Yes, after working on this problem for a week, I can see that it isn't a good to enable or to sign in as Root.  Now I want to not have to sign in as Root.

Here is my original problem:  I can boot up until I get: GConf error. failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or that you have stale NFS locks due to a system crash. Details- 1: Could not send message to GConf Daemon:Message did not receive a reply (timeout by message bus)
  
.....which I have compounded by needing a password for Root.  Now I get a .ICEauthority error.

Hair is turning grey.  Thanks.

---

### Post by spcwingo on 2010-04-11
> **LearningPerson said:**
> Do you mean at the    sh:grub:    command line

or the  <username>: ~#        command line?

I can get back to grub by typing "e" at my grub menu.....which still comes up altho it takes me only to the rotating circle as I have a Gconfig problem.

No, not at the GRUB shell.  In your GRUB menu there should be an entry labeled "recovery mode", "fix broken system" or something to that effect.  Choose that one to boot.  After booting into that one there should be an option to "quit to root shell" or something like that.  At that prompt enter the command that you listed:

```
sudo passwd -l root
```

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> No, not at the GRUB shell.  In your GRUB menu there should be an entry labeled "recovery mode", "fix broken system" or something to that effect.  Choose that one to boot.  After booting into that one there should be an option to "quit to root shell" or something like that.  At that prompt enter the command that you listed:

```
sudo passwd -l root
```

Yes, I know which you mean and will try it later this evening.  

Thanks!

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> No, not at the GRUB shell.  In your GRUB menu there should be an entry labeled "recovery mode", "fix broken system" or something to that effect.  Choose that one to boot.  After booting into that one there should be an option to "quit to root shell" or something like that.  At that prompt enter the command that you listed:

```
sudo passwd -l root
```

When I did what you suggested, I was asked to "give root password for maintenance" and I gave the password I had noted for root.  It said it was incorrect.  

When I am passworded into the :~$ directory, is there any command I can give to go to shell that might work?

---

### Post by spcwingo on 2010-04-11
If that didn't work try this:

At a terminal that you're logged into type the same command, but enter _your_ password instead of the root password.  Let me know if that gets it.

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> If that didn't work try this:

At a terminal that you're logged into type the same command, but enter _your_ password instead of the root password.  Let me know if that gets it.

Um, I maade my password and the root password the same.

---

### Post by LearningPerson on 2010-04-11
> **spcwingo said:**
> If that didn't work try this:

At a terminal that you're logged into type the same command, but enter _your_ password instead of the root password.  Let me know if that gets it.


I could go back and change it for root and then try it?

---

### Post by spcwingo on 2010-04-11
> **LearningPerson said:**
> I could go back and change it for root and then try it?

You can try it, but I doubt it will have any effect.  I am at a loss of what to try next.  Hopefully someone else a little more experienced in these matters will drop in soon.  Sorry I couldn't get it going for ya. :(

---

### Post by LearningPerson on 2010-04-12
Thanks anyway.  I also tried    
sudo -i 

which put me to 
root@username:~#  sudo passwd -l root     

to no avail.

---

