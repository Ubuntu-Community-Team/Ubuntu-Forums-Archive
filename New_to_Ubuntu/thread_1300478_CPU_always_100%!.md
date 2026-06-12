---
title: "CPU always 100%!"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by hotmail@yahoo.com on 2009-10-25
Hi everyone,

I recently updated ubuntu to 9.04. I see that my CPU is always 100% in use. I don't know why its burning my CPU so much even when I'm not running anything.

When I go to System>admnistrator>system monitor>Resources tab I see its full.

I am running an Intel centrino dual core 1.83 GHZ cpu on my laptop. Is there a quick fix for it? I hope I am not burning my CPU that I am decreasing its life.

---

### Post by laidback on 2009-10-25
I don't know the answer I'm afraid but for comparison mine is running at 6-12% whilst I'm using the forum, practically asleep. The only thing that comes to my mind is whether the system is doing something like indexing the files etc. If you look in the Processes tab of System Monitor you should be able to spot what's running which might give you an idea.  Sorry I can't be more helpful.

---

### Post by jobyer on 2009-10-25
[COLOR=Blue]Oh,Brother same problem and + problem some Tool not open also. Wait brother Some one come to help us.Or Change it.[/COLOR]

---

### Post by hotmail@yahoo.com on 2009-10-25
> **laidback said:**
> I don't know the answer I'm afraid but for comparison mine is running at 6-12% whilst I'm using the forum, practically asleep. The only thing that comes to my mind is whether the system is doing something like indexing the files etc. If you look in the Processes tab of System Monitor you should be able to spot what's running which might give you an idea.  Sorry I can't be more helpful.


Thanks for responding. Here are the list of what's running.

dabus-deamon - 31%

Gnome-system monitor - 3%

python - 21 %

trackered - 12%

trackered-indexer - 15%

don't add up to 100% (strange)

they keep fluctuating so this might not be actual but i don't know why its taking 100% even at startup :(

---

### Post by laidback on 2009-10-25
On mine dabus-daemon is sleeping
Gnome-system monitor is running
python is sleeping

don't have the others at all!

---

### Post by Faolan84 on 2009-10-25
in the system monitor:
View > All Processes

Then order the list so it shows what processes are consuming resources.
That is weird dbus-daemon is doing so much.

Also, what applications do you have running?

---

### Post by lovinglinux on 2009-10-25
This is usually caused in Jaunty by vino-server. Go to "System >> Preferences >> Startup Applications" and disable **Remote Desktop**, then reboot.

---

### Post by philinux on 2009-10-25
> **hotmail@yahoo.com said:**
> Thanks for responding. Here are the list of what's running.

dabus-deamon - 31%

Gnome-system monitor - 3%

python - 21 %

trackered - 12%

trackered-indexer - 15%

don't add up to 100% (strange)

they keep fluctuating so this might not be actual but i don't know why its taking 100% even at startup :(

Trackerd is also a known culprit. It has been dumped from the default intall in 9.04. It is still in the repo though. It can be tamed by adjusting its settings. Most people have uninstalled tracker.

---

### Post by lovinglinux on 2009-10-25
> **philinux said:**
> Trackerd is also a known culprit. It has been dumped from the default intall in 9.04. It is still in the repo though. It can be tamed by adjusting its settings. Most people have uninstalled tracker.

Yep, I forgot that. I used to removed it as soon as a new Ubuntu was installed.

---

### Post by hotmail@yahoo.com on 2009-10-25
Lovinglinux and phillinux,

Thank you so much. I removed the tracker from startup and removed it from add or remove program. Also i removed the remote desktop. The CPU is normal now. 14% in use and  I only have Firefox running. Thank you guys.


Another problem I am facing. Take a look at the screenshot.



It pops up every time I boot. Any suggestion?


Also why do I always get this wireless network authorization? It asks me to enter my network key every time and says I have some kind of default  keyring and I need a password to unlock it. I don't remember setting password.

---

### Post by lovinglinux on 2009-10-25
CPU scaling issue:

Removing the CPU scaling applet from the panel should make the warnings stop. There is a fix tho. Google for [CPU frequency scaling unsupported site:ubuntuforums.org](http://www.google.com/search?q=CPU frequency scaling unsupported+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) 

**keyring issue**

In Jaunty:

> **vanshark said:**
> 
The keyring password can be changed (or removed) in Applications/Accessories/Passwords and Encryption Keys. 

ON the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password".

Previous releases:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by hotmail@yahoo.com on 2009-10-25
Thanks, I was able to fix the keyring issue or I hope I fixed it. Haven't rebooted yet. 

Still no luck with the CPU frequency scaling error. I checked google but I don't find an exact solution.

Thanks anyway.

---

### Post by laidback on 2009-10-25
The pop up is because you have the add on called CPU Frequency Scaling Monitor loading, it sits at the top of your screen and tells you how much CPU capacity is being used, % or some other figure that I cannot remember. But, your CPU doesn't allow you to control this aspect, it's just as it is. 

It's an Add to Panel option. Remove it if it annoys you.

---

