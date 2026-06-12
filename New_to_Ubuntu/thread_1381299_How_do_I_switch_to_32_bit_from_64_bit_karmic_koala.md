---
title: "How do I switch to 32 bit from 64 bit karmic koala?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by milkytea on 2010-01-14
Hi, I installed the 64 bit version of karmic koala and would like to switch to 32 bit.  Is there an easier way to do this besides burning a cd and installing it from there?   If install from a cd will it re-write everything?

Thanks in advance!

---

### Post by running_rabbit07 on 2010-01-14
Nope. The only way to do it, is to reinstall. Is there a particular reason you need to change? Maybe someone here can help you if you need it.

---

### Post by tom.swartz07 on 2010-01-14
> **milkytea said:**
> Hi, I installed the 64 bit version of karmic koala and would like to switch to 32 bit.  Is there an easier way to do this besides burning a cd and installing it from there?   If install from a cd will it re-write everything?

Thanks in advance!

Sorry, the only way you could switch versions of Ubuntu (or any OS, for that matter) is to re-install the entire OS.

Is there a particular reason you dont like the 64 bit version? If you are having problems with something, I would be more than willing to help!

---

### Post by Cabs21 on 2010-01-14
2 ways to do this.

1: Backup your settings, data, and Preferences. Then do a fresh install wiping the HDD clean and reinstalling.
2: Run gParted and make another partition for your 32-Bit Install and install and make sure you chose that partition when installing.  Also back up your settings, data, and preferences.

I did Idea 2 before idea 1 to make sure A my system could handle 64-bit and B that I could import my settings, data, and preferences from my 32-bit installation.  (was not a simple thing took a little bit of time)  After that I ended up breaking my GRUB Booter and said screw it and created a fresh Install of 64-bit.

what hard ware do you have at your disposal?

---

### Post by J V on 2010-01-14
I could let you reinstall ubuntu losing all your stuff in the proccess, and laugh at you when you come crying back that we didn't warn you... nevertheless, going for the 32bit OS won't change anything, your machine is still 64bit, 32bit apps will still behave the same way...

---

### Post by milkytea on 2010-01-15
Thank you everyone for your responses!

Basically I haven't been able to run Second Life since installing 9.10 64 bit.  It worked fine on 9.04!  I was hoping there was some sort of way to revert to a previous ubuntu version so I wouldn't have to bother monkeying around.  
[B]
So this is what the READ ME for linux SL says: [/B]

"The Second Life Linux client entirely runs out of the directory you have
unpacked it into - no installation step is required.

Run ./secondlife from the installation directory to start Second Life."

**And this is what happens when I do what I think I'm supposed to be doing: **

abi@Hamhock:~/Desktop$ ./secondlife
bash: ./secondlife: No such file or directory

Yes it's stored on the desktop.  And everything else seems to run fine.

---

### Post by tom.swartz07 on 2010-01-15
> **milkytea said:**
> Thank you everyone for your responses!

Basically I haven't been able to run Second Life since installing 9.10 64 bit.  It worked fine on 9.04!  I was hoping there was some sort of way to revert to a previous ubuntu version so I wouldn't have to bother monkeying around.  
[B]
So this is what the READ ME for linux SL says: [/B]

"The Second Life Linux client entirely runs out of the directory you have
unpacked it into - no installation step is required.

Run ./secondlife from the installation directory to start Second Life."

**And this is what happens when I do what I think I'm supposed to be doing: **

abi@Hamhock:~/Desktop$ ./secondlife
bash: ./secondlife: No such file or directory

Yes it's stored on the desktop.  And everything else seems to run fine.

is it stored in a *folder* on the desktop? you might have to store everything in a private folder and cd into the folder to run the app

```
ls ~/Desktop
```

---

### Post by running_rabbit07 on 2010-01-15
It is best to put it in your home folder so you don't have to redirect to the folder and don't forget to use chmod. ```
sudo chmod +x <filename>
```

---

