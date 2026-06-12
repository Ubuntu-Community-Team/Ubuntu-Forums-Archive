---
title: "Ubuntu not responding"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by nnsandhya on 2011-05-05
Hi,

I am completely new to Ubuntu and yesterday I got a upgrade popup and I tried to upgrade and later i shut down the machine and this morning I computer is not responding. I get a blank screen and the mouse even does not move. 

Can anyone help me what can be done so my laptop wakes up?

Thank you,
Sandhya

---

### Post by wigout on 2011-05-07
Sorry for your troubles.

I'm not sure what's happening here. 

Try (from [https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key):]("https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key%29:")

```
**"Raising Elephants" mnemonic device**

 A common use of the magic SysRq key is to perform
 a safe reboot of a  Linux computer which has otherwise 
locked up. This can prevent a [fsck]("https://secure.wikimedia.org/wikipedia/en/wiki/Fsck") being required on 
reboot and gives some programs a chance to save 
emergency backups of unsaved work.[[5]]("https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key#cite_note-4") The QWERTY 
(or AZERTY) [mnemonic]("https://secure.wikimedia.org/wikipedia/en/wiki/Mnemonic") 
"**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring", 
"**R**eboot **E**ven **I**f **S**ystem **U**tterly **B**roken" 
or simply remembering the word "BUSIER" backwards, 
are often used. It stands for:
 un**R**aw      (take control of keyboard back from [X]("https://secure.wikimedia.org/wikipedia/en/wiki/X_Window_System")),
  t**E**rminate (send [SIGTERM]("https://secure.wikimedia.org/wikipedia/en/wiki/SIGTERM") to all processes, allowing them to terminate gracefully),
  k**I**ll      (send [SIGKILL]("https://secure.wikimedia.org/wikipedia/en/wiki/SIGKILL") to all processes, forcing them to terminate immediately),
   **S**ync     (flush data to disk),
   **U**nmount  (remount all filesystems read-only),
 re**B**oot.
In practice, each command may require a few seconds to complete, 
especially if feedback is unavailable from the screen due to a freeze or  
display corruption.

```Try holding each letter REISUB, one at a time, for about five seconds each before moving on to the next. This more safely shuts down your pc.

Failing that, if you'd like to force the issue, holding the power button down on your laptop for ten seconds will cause it to power down. Try powering up again and see where you're at.

On my notebook computers I've noticed frequently that on some installs of ubuntu and certain notebooks suspend and sleep mode operate poorly. Often times the computer wakes but the screen refuse to become live again.

---

