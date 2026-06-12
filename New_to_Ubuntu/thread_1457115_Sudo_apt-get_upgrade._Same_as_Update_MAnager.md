---
title: "Sudo apt-get upgrade. Same as Update MAnager?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by cK` on 2010-04-18
Hello everyone,

I do not like updating my OS from the update manager because it after updating and rebooting my computer gives me two OS to boot from, They are both LUCID 10.04 unbunt but one is a different version than the other.

Anyway this bothers me and i only want to be able to choose from Ubuntu or windows not unbuntu1 ubuntu2 windows.


Is sudo apt-get upgrade the same as the update manager?

If someone could please let me know how to do the same thing that the update manager does but from the terminal that  would be great!

THanks!

---

### Post by wojox on 2010-04-18
You have two kernels installed which is good.

To run updates from the terminal:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by uberlinuxnerd on 2010-04-18
> **cK` said:**
> 
Is sudo apt-get upgrade the same as the update manager?


Yep! :)

---

### Post by cK` on 2010-04-18
Why is having two kernels good? 

When i used sudo apt-get update then sudo apt-get ugrade it did not give me two kernels.

I never did sudo apt-get distro-upgrade through.

Is that what gives me two kernels?

---

### Post by new_tolinux on 2010-04-18
No, once in a while there is a kernel-update.
But because that new kernel _may_ fail in your case, the old kernel is left so you can fall back on that one.

---

### Post by wojox on 2010-04-18
It's good to have two in case the newest one borks out. You have two kernels because of an upgrade you ran.

---

### Post by cK` on 2010-04-18
Oh ok.

 I still don't understand why the update manager gave me two kernels but using sudo get-apt update && sudo apt-get upgrade did not.

And why did running it manually not update the update manager?

THanks for all your replies i appreciate it very much!

---

### Post by new_tolinux on 2010-04-18
> **cK` said:**
> Oh ok.

 I still don't understand why the update manager gave me two kernels but using sudo get-apt update && sudo apt-get upgrade did not.

And why did running it manually not update the update manager?

THanks for all your replies i appreciate it very much!
Updates for the update-manager are generally done once per day (by the way, I'm not using Lucid yet).
Using the command-line update/upgrade would also give you an extra kernel if there's a kernel update.

The reason the command-line upgrade didn't give you an extra kernel yet, is because kernel-updates don't come once-a-day. For me (about 1/2 year of Jaunty yet) I only have 4 kernels in my grub yet. That's the first (installed) kernel + 3 updates. Although while Lucid is still beta, they can come more often than that.

---

### Post by Teber on 2010-04-18
it's good to have at least one kernel as backup for in case the latest kernels fails. if the list should really start looking like it's endless, one may remove the oldest kernels. 

as to how remove older kernels, the search function would be helpful. however, i would suggest you to do some reading of the ubuntu docs first. both the official and the community provided ones.

---

### Post by cK` on 2010-04-18
Oh ok, that explains alot.

I was really against having two because it made me feel "uneasy" lol.

Thanks for taking the time to explain these things to me.


Have a great day!


Edit: Ye unfortunately i all ready deleted it.

Hopefully i will not regret it later.

Thanks again everyone.

---

### Post by new_tolinux on 2010-04-18
> **cK` said:**
> Edit: Ye unfortunately i all ready deleted it.

Hopefully i will not regret it later.

You probably won't.
If the new kernel is working the way it should, you'll never miss the "old" kernel.

That said, there's only a very small chance that you would like to go back to the "old" kernel once your system did boot up correct after a kernel-update. You'll probably discover errors in the new kernel (if any) during the first few hours you use it.
After that there's almost no chance you want to go back to using the old kernel.

---

### Post by CharlesA on 2010-04-18
> **cK` said:**
> Oh ok.

 I still don't understand why the update manager gave me two kernels but using sudo get-apt update && sudo apt-get upgrade did not.

And why did running it manually not update the update manager?

THanks for all your replies i appreciate it very much!

The kernel is usually only upgraded if you run apt-get dist-upgrade.

Update manager does this automatically.

---

### Post by Elfy on 2010-04-18
> **CharlesA said:**
> The kernel is usually only upgraded if you run apt-get dist-upgrade.

Update manager does this automatically.

I rarely use update manager - a sudo apt-get update &&sudo apt-get upgrade gets kernel upgrades just fine.

---

### Post by CharlesA on 2010-04-18
> **forestpiskie said:**
> I rarely use update manager - a sudo apt-get update &&sudo apt-get upgrade gets kernel upgrades just fine.

Interesting. If there is a kernel upgrade available, and I run sudo apt-get upgrade, it usually tells me that xx packages were not install or xx packages were held back.

Doing a dist-upgrade fixes that. *shrug*

Maybe I am doing something wrong.

EDIT: Running Ubuntu 2.6.31-20-server.

---

### Post by barney385 on 2010-04-18
apt-get update &#8211; refresh available updates
apt-get upgrade &#8211; upgrade all packages
apt-get dist-upgrade &#8211; upgrade with package
replacements; upgrade Ubuntu version
apt-get install pkg &#8211; install pkg
apt-get purge pkg &#8211; uninstall pkg
apt-get autoremove &#8211; remove obsolete packages
apt-get -f install &#8211; try to fix broken packages
dpkg --configure -a &#8211; try to fix broken
packages
dpkg -i pkg.deb &#8211; install file pkg.deb
(file) /etc/apt/sources.list &#8211; APT repository

---

### Post by barney385 on 2010-04-18
lsb_release -a &#8211; get Ubuntu version
uname -r &#8211; get kernel version
uname -a &#8211; get all kernel information

---

