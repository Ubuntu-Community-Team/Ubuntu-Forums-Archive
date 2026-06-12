---
title: "Need more space"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by timbob1957 on 2009-07-21
This Linux and Ubuntu has me going in circles...ok...heres my problem...I bought a dell mini 9 which has only a 4 gb hard drive...I have not installed anything on it, just use it for internet for traveling...but...all the updates from the program manager has topped off my hard drive...and now I cant get on the internet or finish installing the last updates I got....How do I free up some disk space..I've gone into add and remove to no avail..maybe I should just stick with windows...can someone give me a little advice

---

### Post by c0mput3r_n3rD on 2009-07-21
> **timbob1957 said:**
> This Linux and Ubuntu has me going in circles...ok...heres my problem...I bought a dell mini 9 which has only a 4 gb hard drive...I have not installed anything on it, just use it for internet for traveling...but...all the updates from the program manager has topped off my hard drive...and now I cant get on the internet or finish installing the last updates I got....How do I free up some disk space..I've gone into add and remove to no avail..maybe I should just stick with windows...can someone give me a little advice

Did you install Ubuntu for netbooks or Ubuntu Desktop version?

---

### Post by timbob1957 on 2009-07-21
I did not install it...it came already installed on the computer

---

### Post by timbob1957 on 2009-07-21
it was already installed from dell

---

### Post by c0mput3r_n3rD on 2009-07-21
Well you only have a 4Gb HDD.  Ubuntu takes up less space than Winblows.  Those little netbooks are really just for surfing the internet.  You can always download an older (smaller) version.  Make sure it's an Ubuntu Netbook distro.

---

### Post by timbob1957 on 2009-07-21
I get this message when I go to synaptic package manager
E:dpkg was interrupted, you mmust manually run 'dpkg--configure-a' to correct the problem.

---

### Post by Temposs on 2009-07-21
hi tombob,
   Go into firefox. Go to Edit->Preferences. Click the Privacy Tab. Under the Private Data section, click the "Clear Now" button. Check as many of the items there as you care to, but make sure you have "Cache" checked. This should clear some hard drive space for you.

Next, in the firefox address bar, type:

```
about:config
```

In the Filter search, type:

```
cache
```

You will see many less items listed now. Find the browser.cache.disk.enable option, and change its value from "true" to "false", by double-clicking on it, probably. This action should prevent firefox from filling your hard drive with saved websites. It may make your browsing a little slower. Alternatively, you can make the value of the browser.disk.capacity lower from its original value, and that will make firefox take up less space for its caching.

Another thing to do is go to System->Administration in the menu and run the Computer Janitor. Have it clean up extra files in your computer that you don't need.

:-)

---

### Post by Temposs on 2009-07-21
> **timbob1957 said:**
> I get this message when I go to synaptic package manager
E:dpkg was interrupted, you mmust manually run 'dpkg--configure-a' to correct the problem.

To fix this problem(which was caused by an installation process being interrupted), you must open a terminal. In the menu, open a terminal by navigating Applications->Accessories->Terminal.

Now you will have a little text prompt. Please type:

```
dpkg --configure -a
```

Hopefully this will fix your problem with synaptic :-)

---

### Post by Temposs on 2009-07-21
Another space-freeing option is to open the terminal as in the above post, and type this:

```
sudo apt-get autoremove
```

This just uninstalls packages that Ubuntu knows aren't needed by anything. It's safe.

---

### Post by mgranet on 2009-07-21
Don't forget to uninstall the old kernels (via your package manager). An old kernel can take up several hundred megs of space.

EDIT: Type **uname -a** into a terminal. Note your kernel version. Make extra sure not to remove that version when you are unintsalling the old kernels ;)

---

### Post by davidw19125 on 2009-07-29
Hi can you use computer janitor to delete a deb package and still not take the program off your computer to make more disk space?
                                                    Davidw19125

---

### Post by Temposs on 2009-07-29
That is right. Computer janitor will remove the deb package but it will not take the program off your computer.

---

### Post by davidw19125 on 2009-07-29
Thanks i thought that was how to do it but I was not to sure I only had ubuntu 9.4 on my computer now for three weeks. It is a lot different then using windows xp but it boot up a lot faster and gets on the web a lot faster to. 
                         Thanks for your help. 

                                                       Davidw19125

---

### Post by mikechant on 2009-07-30
Assuming you have an SD card slot and maybe don't use it for anything much else, you might want to use it as a permanant extra disc drive. You could move your /home over to it for example. You would probably want a class 6 SD card (fastest spec) - a 4Gb one shouldn't cost much.
I haven't tried this myself but I've seen comments from others claiming it works fine (i.e. fast enough).

---

