---
title: "Upgrading Lucid to Maverick"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by gavdari on 2010-10-10
It's the first time that I'm a Ubuntu user and a new version is released. So, for upgrading from lucid to maverick, should I download the whole image and install a fresh version or can I upgrade the lucid I have? I don't want to lose the config I have here. Besides, I have a slow connection and I'd prefer smaller download sizes.

---

### Post by dancer_69 on 2010-10-10
You can upgrade to maverick your current installation.
You must push Alt+F2 and write update-manager -d.
But until now only the RC version is available. I hope that stable version will be soon available for upgrade.

---

### Post by da burger on 2010-10-10
I believe once the stable version becomes available you will be able to upgrade using upgrade manager normally. It should even pop up to tell you about it :)

---

### Post by Deuce1912 on 2010-10-10
The new release of Maverick 10.10 is now available. Just go to the update-manager under System > Administration > Update Manager, and you should see it as an option to upgrade at the top of the window. 

If not, then open up a terminal or hit Alt + F2 and type in "update-manager -d" (no quotes) like dancer said.

Good luck.

Deuce

---

### Post by redbook4574 on 2010-10-10
> **Deuce1912 said:**
> The new release of Maverick 10.10 is now available. Just go to the update-manager under System > Administration > Update Manager, and you should see it as an option to upgrade at the top of the window. 

If not, then open up a terminal or hit Alt + F2 and type in "update-manager -d" (no quotes) like dancer said.

Good luck.

Deuce

Take my advice, wait a couple of days the servers will be packed today.

---

### Post by eferrr on 2010-10-10
Quick question, piggybacking on this thread:

Is the update to 10.10 available through Update Manager?  I'm currently running 10.4 LTS, and Update Manager tells me there are no new updates.

Or is it just that that the new version isn't YET available through update manager?

My main concern is that all the official Ubuntu/Canonical info I see out there mentions that current Ubuntu users can upgrade through Update Manager.

Thanks in advance for ANY info anyone out there can provide!

--Ed

---

### Post by beew on 2010-10-10
If you have PPAs, third party programs and propietary drivers you should check a bit before you upgrade. My understanding is that the upgrader only works well if you have a "pristine" system .

---

### Post by migs73 on 2010-10-10
Check the settings of your update manager. In the updates tab you should have the release upgrade set to normal releases. Otherwise it'll be ignored.

---

### Post by eferrr on 2010-10-10
> **migs73 said:**
> Check the settings of your update manager. In the updates tab you should have the release upgrade set to normal releases. Otherwise it'll be ignored.

That did the trick -- I had it set for "Long-Term Releases Only."  

Thanks, Migs!

---

### Post by Ve5ahchoo8ah on 2010-10-10
I have same problem!
Lucid doesn't show any upgrades! when I use "update-manager -d" it gives me RC version!
I have my upgrade setting to Normal
I don't know what else can I do!

---

