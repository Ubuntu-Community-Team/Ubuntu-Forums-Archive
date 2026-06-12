---
title: "[SOLVED] A proper way to install latest ndiswrapper"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by dda on 2008-06-26
Hello,

Some time ago I figured out that stock Gutsy ndiswrapper (1.42 at that moment) periodically caused OOPS in my system (64bit, driver neti2220x64). I tried current version (1.52 at that moment) and it worked very well, no OOPS at all. Recently I saw the same OOPS agan, and then I discovered that ndiswrapper module was old (1.43). I guess it came from kernel upgrade. 

Now I wonder how to prevent it, i.e., how to automatically keep currently installed version from being replaced with older during automatic kernel upgrades?

Thanks!
Dmitry.

---

### Post by kevdog on 2008-06-26
You might need to install from source or svn.  I dont think if you upgrade however ndiswrapper is part of that process.

---

### Post by dda on 2008-06-26
Hi,
> You might need to install from source or svn.
I did:
> I tried current version (1.52 at that moment) and it worked very well
The version from source was installed. And the kernel module (ndiswrapper.ko) was overwritten by kernel-modules upgrade.

---

### Post by kevdog on 2008-06-26
Sorry to hear about that with the upgrade,  so why don't you just compile and reinstall ndiswrapper again?  It should take like 30 seconds?

---

### Post by dda on 2008-06-26
Of course I did it, and installed the current (1.53) version. But before i did it, I experienced a system crash, because some automatic upgrade of kernel modules silently replaced my ndiswrapper, and I did not notice it, until the system crashed with all my applications open. That's strange that Gutsy still has version 1.43, while the current is 1.53. So, I just wanted to protect myself from such thing in the future (when Gutsy will upgrade to, say, 1.44, and overwrite my version again). 

Any other ideas? Make the kernel module file (ndiswrapper.ko) read-only? Looks like a hack...

Regards,
Dmitry.

---

### Post by dmizer on 2008-06-26
> **dda said:**
> Of course I did it, and installed the current (1.53) version. But before i did it, I experienced a system crash, because some automatic upgrade of kernel modules silently replaced my ndiswrapper, and I did not notice it, until the system crashed with all my applications open. That's strange that Gutsy still has version 1.43, while the current is 1.53. So, I just wanted to protect myself from such thing in the future (when Gutsy will upgrade to, say, 1.44, and overwrite my version again). 

Any other ideas? Make the kernel module file (ndiswrapper.ko) read-only? Looks like a hack...

Regards,
Dmitry.

if you compiled ndiswrapper from source, you will need to recompile every time you get a kernel update.  when you compiled the new version of ndiswrapper, you compiled it against one kernel only.  so your version is not getting overwritten or replaced, it's simply not available for your new kernel, and the new kernel falls back to the ubuntu supported version.

best bet to avoid this, is to simply uninstall the ubuntu version of ndiswrapper so it doesn't get upgraded with the kernel. you won't have working internet after a kernel update, but you also won't have problems with your computer locking.

packages in the repos are old because:
someone has to take the time to build and test a debian package against the source.

while this may sound simple, ndiswrapper is not built or maintained by ubuntu.  it has it's own separate maintainers and release schedule.  so, someone from the ubuntu team has to build it and submit it for testing (you wouldn't want a broken package would you), then the package has to be signed, approved, and uploaded with a scheduled kernel update.

this is fairly easy to accomplish if you only focus on ndiswrapper, but with the thousands of packages (all with the same issues) available in the ubuntu repos, you're looking at a massive undertaking that the package team can barely keep up with.

because of this, it's a trade off.  you either get tested packages and a stable system, or you get current and untested software that's potentially (and likely) buggy.

---

### Post by dda on 2008-06-27
dmizer, thanks a lot for your reply. Everything is clear now. I will remember to reinstall my modules after each kernel upgrade.

Regards,
Dmitry.

---

### Post by kevdog on 2008-06-27
If you keep the svn source of ndiswrapper available, its really easy to update, and then simply reinstall.  It should take just a few seconds (and hence you get the latest and greatest svn -- I've never had a problem with svn sources specifically with ndiswrapper, however I guess you are at slightly increased risk of instability).

I wrote a tutorial once on how to install ndiswrapper from svn.  Basically checkout the modules something like this:

```

cd ~
mkdir src
cd src
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ndiswrapper-svn
cd ndiswrapper-svn

make distclean
make
sudo make install

```


Verify installation with:
```

ndiswrapper -v

```

Proceed to load the windows driver and insert the module into the kernel:
sudo ndiwrapper -l <windows_driver.inf>
sudo modprobe ndiswrapper


If at any time you need to update the sources (which I do frequently):
```

cd ~/src/ndiswrapper-svn
svn up

sudo rmmod ndiswrapper
make distclean
make
sudo make install

```


Just remember that ndiswrapper is a custom kernel module -- meaning that by default it was not compiled into the kernel.  If you ever compile your own kernel from vanilla sources this will make more sense to you.  When you update your kernel, just remember your custom kernel module is no longer valid, and needs to be recompiled against the header files of the new kernel and then reinserted into the kernel.  Hence the pitfalls or joys of custom kernel modules.

---

### Post by dda on 2008-06-27
Thanks kevdog! I do not update often, and I prefer not to change system software (like ndiswrapper) unless I have reasons to do it. But with periodical Ubuntu kernel updates, I will have to do it. The procedure is clear now.

Best regards,
Dmitry.

---

