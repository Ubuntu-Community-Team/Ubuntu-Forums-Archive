---
title: "No upgrade button in Upgrade Manager"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by linuxnoob53108 on 2009-04-30
Alright, so I tried to follow the upgrade directions to move to 9.04 for 8.10, but I have hit the check button multiple times in the upgrade manager and I never get and upgrade button for the new version, is there another way to upgrade or can someone just give me the terminal commands to do it from there?? Thanks!!

---

### Post by TheNosh on 2009-04-30
you can always back up your data and do a clean install of 9.04

in most cases i would try and get the upgrade function to work, but if you want ext4 you're gonna need a clean install anyway, and ext4 is the way of the future so why fight it? :wink:

---

### Post by DustyMP on 2009-04-30
You can try this, I don't know if it will work but it got me from Hardy to Intrepid. Open a terminal and type:

sudo apt-get install dist-upgrade

Enter your password and it should run the upgrade.

---

### Post by SentientFluid on 2009-04-30
> **linuxnoob53108 said:**
> Alright, so I tried to follow the upgrade directions to move to 9.04 for 8.10, but I have hit the check button multiple times in the upgrade manager and I never get and upgrade button for the new version, is there another way to upgrade or can someone just give me the terminal commands to do it from there?? Thanks!!

First thing to note is that you can only upgrade to 9.04 from 8.10 and I believe you need to have all the regular updates installed.  Assuming you all that has been done, quit all apps and try this...

1. Press Alt+F2.

2. In the command box type the code below and press Enter.```
update-manager -d
```

3. Update Manager should open up you should see > New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.

The above is for Ubuntu Desktop. If you have installed Ubuntu Server the process is different.

---

### Post by nandemonai on 2009-04-30
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

If for some reason you're not getting the upgrade notification you can always hit alt-F2 (in gnome) then type 

```
update-manager -d
```

or

```
update-manager --dist-upgrade
```

If all else fails try the server upgrade option which is a lot safer than a apt-get dist-upgrade.

Install update-manager-core if it is not already installed:

```
sudo apt-get install update-manager-core
```

Launch the upgrade tool:

```
sudo do-release-upgrade
```

Follow the on-screen instructions.

You might want to check on your sources if you're having troubles upgrading.

---

### Post by DustyMP on 2009-04-30
> **nandemonai said:**
> 

If all else fails try the server upgrade option which is a lot safer than a apt-get dist-upgrade.



Just for my edification what do you mean by safer?

---

### Post by Didius Falco on 2009-05-01
The easiest way to do it is to go to **System/Administration/Software Sources**, go to the **Updates **tab, and change the  "Release Upgrade" section at the bottom to **Normal releases**.

It will then offer to Upgrade your setup to 9.04 or whatever the next release is from your current version; i.e., you can't skipfrom 8.04 directly to 9.04.

Make sure you:

1. Disable all 3rd party software sources

2. Remove any Proprietary graphics drivers

3. Have applied all the updates to your current version.

4. Have backed up all your data.

In the case of an upgrade to Jaunty, if 3D is important to you, confirm that your card will work in 3D mode under Jaunty. There have been a lot of people with cards that have been dropped to "legacy cards" that can't run Jaunty in 3D who have upgraded and immediately wanted to "downgrade".

Downgrading isn't possible to do. You have to back up your data and reinstall. Check first and save yourself some hassle if 3D is a high priority.

If you are happy with an Open Source 2D driver that works very well in 2D but doesn't support 3D at this time (they are working on it, but there are no guarantees when it will happen), then follow the above precautions and upgrade away!!

---

### Post by wlraider70 on 2009-05-01
is it possible that there is an error in the "sources" like something got diabled?

---

### Post by josaphat on 2009-05-01
Make sure that you've enabled Normal Releases in the Updates Tab under System->Administration->Software Sources.

---

### Post by nandemonai on 2009-05-01
> **DustyMP said:**
> Just for my edification what do you mean by safer?

In my experience apt-get dist-upgrade *used* to work, or rather I was lucky in that I hadn't had problems with it until I attempted a LTS to LTS upgrade.

The system well and truly borked up. It was, in my case to do with /dev/ references for hard disks changing from hdX to sdX. The apt-get method failed to realise this and while the system still booted due to UIDs being used it was a real mess regardless. I ended up having to clean install Hardy.

Essentially, update-manager / update-manager-core as quoted on the official upgrade documentation is smart enough to realise such changes and adapt for them, so it's much safer to do it that way.

I found out the hard way ;)

---

### Post by DustyMP on 2009-05-01
Thanks for the info Nandemonai!

---

### Post by rsgrimes on 2009-05-12
> **josaphat said:**
> Make sure that you've enabled Normal Releases in the Updates Tab under System->Administration->Software Sources.

I have this same problem on one machine - I cannot upgrade from 8.04 to 8.10!  The Upgrade button does not show up no matter what I do.  I've tried everything that makes sense in this thread (specifically, of course, enabled Normal Releases in the Software Sources).

So, what would cause the Upgrade button to not be shown?  Is there a log file that I can check that might tell me what is wrong?

Thanks for any help!
-Bob

---

### Post by rajeev1204 on 2009-05-12
```
sudo update-manager -d
```

This is the best way to do a distribution upgrade.

Or if this doesnt work due to some reason.

```
sudo apt-get dist-upgrade
```




regards
rajeev

---

### Post by rsgrimes on 2009-05-12
I tried it before - really, I swear I did - but to be 110% sure, I tried "sudo update-manager -d" yet again, and the Upgrade button showed up!!!  Don't know why it worked this time, but who cares?

Thanks, Rajeev!

---

### Post by qneill on 2009-09-18
> **rsgrimes said:**
> I tried it before - really, I swear I did - but to be 110% sure, I tried "sudo update-manager -d" yet again, and the Upgrade button showed up!!!  Don't know why it worked this time, but who cares?

Thanks, Rajeev!

@rsgrimes, you aren't crazy, I did the same thing, only after the second time that I ran "update-manager -d" did I get a button.
I'm wondering if some cached files were refreshed the first time or something.

---

### Post by rcoe74 on 2009-12-07
Exactly the same for me I had to do sudo update-manager -d multiple (at least 4) times before the 9.10 button showed up :D

---

