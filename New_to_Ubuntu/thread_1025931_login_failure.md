---
title: "login failure"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by judydogan on 2008-12-30
I fell asleep installing the latest ubuntu 8.10.   It continued the install without any input from me.   Now I cant login because i have no idea what my login name or password is.  How do I find out?  I am using this for the very first time.

---

### Post by stderr on 2008-12-30
I'm not really sure how it would have installed without requesting a uname & password. Are you sure you didn't enter one and then fall asleep? ;)

However, whatever happened, I would imagine the easiest solution if you really can't log in would be to simply reinstall over your current installation, since you've only just installed it anyway. 

It *may* be possible to rainbow table crack a password relatively easily depending, but I'm almost 100% sure your easiest solution will be a reinstall. Anyway, without a user, I don't even know what password we'd be trying to get... since Ubuntu doesn't make a root account by default, the only other real login account it makes is the user you provide during installation. I can't understand what's happened if you really didn't provide any user account info...

---

### Post by namdung on 2008-12-30
> **judydogan said:**
> I fell asleep installing the latest ubuntu 8.10.   It continued the install without any input from me.   Now I cant login because i have no idea what my login name or password is.  How do I find out?  I am using this for the very first time.

Ubuntu will not install without Username/Password. However, LiveCD doesn't required Username/Password to load.

So are u very sure u didn't enter any username/password because its impossible to install Ubuntu without one?

It might be possible to login as root and change the password. Changing the username may be possible but very difficult process.

I recommend u reinstall Ubuntu. Furthermore, stable Hardy Heron 8.04.2 LTS is releasing on 1/1/2009 for ur service.

---

### Post by judydogan on 2008-12-30
i installed ubuntu with vista.  fell asleep in the process.  it installed itself and i have no clue what my login name or password is    HELP!

---

### Post by zzHanks on 2008-12-30
I don't know if it is the same with Wubi, but you can try: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by decoherence on 2008-12-30
EDIT: i'll leave this here for posterity, but the instructions posted by zzHanks are easier to follow and up to date (guess i haven't had to boot in to recovery mode in a while!)

> i installed ubuntu with vista.

i guess that means you installed with wubi?

does wubi provide a default user/pass? i have no idea.

start booting ubuntu and when prompted, press escape to enter the GRUB menu (watch for it... it'll be quick!)

boot in to recovery mode (probably the second option from the top) and once you get a prompt (ends with #) type

```
cat /etc/passwd
```

one of the last lines should contain your username.

now type

```
passwd *username*
```

where *username* is the name you found in the previous command

it will offer to change the password for the user. type in the password and press enter. NOTE nothing will be displayed as you type the password. this is normal. type it in again and press enter to make sure you got it right. now type
```

shutdown -r now
```

to reboot and hopefully log in!

---

### Post by ghostypaste on 2009-01-18
Hey all,
I did a really stupid thing. I wanted to change my password, and typed into the terminal:
sudo passwd -d username
It then asked for my passowrd, obviously, and then declared "password changed."
CHANGED TO WHAT?

Anyway, the dumb thing was to turn off my computer after this.

I tried to log in again, but any password I try doesn't work. What do I do now? Any ideas, besides reinstall Ubuntu Hardy?

---

### Post by albinootje on 2009-01-18
> **ghostypaste said:**
> 
I tried to log in again, but any password I try doesn't work.

Already mentioned, this is pretty good to use :
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
assuming that Wubi has the "recovery mode" boot option.

---

