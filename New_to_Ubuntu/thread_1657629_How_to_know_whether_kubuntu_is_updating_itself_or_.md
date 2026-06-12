---
title: "How to know whether kubuntu is updating itself or not?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by babloo75 on 2011-01-01
I have installed Kubuntu 10.10 on a computer. But since its installation it has never updated itself (I may be wrong, but unlike Ubuntu which has update manager and regularly updates itself), KPackageKit has never shown any update whenever I have clicked the option "check for new updates".

Is there any way to find out whether Kubuntu is getting updated or not?

---

### Post by Paqman on 2011-01-01
I'm not familiar with kpackagekit. You could try opening a terminal and issuing these commands. To update your list of packages:
```
sudo apt-get update
```
then to install all available updates:
```
sudo apt-get upgrade
```
If you get any errors, post them here and we'll see what we can do for you.

---

### Post by Frogs Hair on 2011-01-01
Check history in KPackage for the latest update information.

---

### Post by babloo75 on 2011-01-01
> **Frogs Hair said:**
> Check history in KPackage for the latest update information.

The history option only shows the list of installed or removed softwares on various dates. Nothing else.

---

### Post by Frogs Hair on 2011-01-01
My mistake I may have wrongly assumed history would contain updates as Ubuntu does.

There is the possibility you have never updated and ;therefore , have no update history .

Will look into Kubuntu update settings.

---

### Post by Frogs Hair on 2011-01-01
This should lead to automatic update settings if you haven't checked already. 

Use KPackageKit: 
K menu -> System -> System Settings -> Add and Remove Software -> Settings -> Edit Software Sources -> Updates -> Automatic Updates

It is possible to install the synaptic package manager and see if any updates are found . This may indicate weather the KPackage Kit is working.

---

### Post by babloo75 on 2011-01-02
So I have installed Synaptic Package Manager. I feel its much better than KPackageKit. It has the option of completely removing leftover stuff of the uninstalled applications. Theres no such option present in KPackageKit.

But how can I know whether my Kubuntu has updated itself since installation or not. Can anyone suggest?
Thanks once again.

---

### Post by Paqman on 2011-01-02
> **babloo75 said:**
> 
But how can I know whether my Kubuntu has updated itself since installation or not. Can anyone suggest?


Do you have a lot of updates waiting to be installed?

---

### Post by babloo75 on 2011-01-03
> **Paqman said:**
> Do you have a lot of updates waiting to be installed?

My system hasn't updated itself since long time. Whenever I click "Check for new updates"..... there has never been any update since installation. Thats why I am worried, how can there be no update since October 2010 version of Kubuntu. 
The screenshot has been attached here with.

Even Synaptic Package manager hasn't shown any update to Kubuntu 10.10.

---

### Post by Zorael on 2011-01-03
Are your software sources configured to properly use the maverick repositories?

Run '**kdesudo software-properties-kde**' and make sure stuff is checked. There's also a tab there for updates.

---

### Post by babloo75 on 2011-01-03
> **Zorael said:**
> Are your software sources configured to properly use the maverick repositories?

Run '**kdesudo software-properties-kde**' and make sure stuff is checked. There's also a tab there for updates.

Can you please tell which options have to be selected: 
Screenshots

---

### Post by Zorael on 2011-01-03
No, that looks about right, actually. Hm.

Try changing server in the first tab, "Download from". Just incase there's something wrong in your sources.list file.

Also, hit Alt+F2 and enter '**notificationhelper**'. Make sure that Upgrade information is ticked. This shouldn't affect KPackageKit not finding any packages to upgrade though.

**edit:** Oh, and head into Service Manager in System Settings and make sure that the KPackageKit service is ticked and running.

If all that fails, do it from a terminal and see if it outputs anything of interest.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

---

### Post by babloo75 on 2011-01-03
> **Zorael said:**
> No, that looks about right, actually. Hm.

Try changing server in the first tab, "Download from". Just incase there's something wrong in your sources.list file.

Also, hit Alt+F2 and enter '**notificationhelper**'. Make sure that Upgrade information is ticked. This shouldn't affect KPackageKit not finding any packages to upgrade though.

**edit:** Oh, and head into Service Manager in System Settings and make sure that the KPackageKit service is ticked and running.

If all that fails, do it from a terminal and see if it outputs anything of interest.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

I followed all the instructions. All are present in 'notificationhelper' as explained by you.
In service manager, KPackageKit is running and ticked.

In the end, Terminal says "sudo aptitude command not found"

---

### Post by Paqman on 2011-01-03
> **babloo75 said:**
> 
In the end, Terminal says "sudo aptitude command not found"

That's because aptitude isn't installed by default any more. Try again with:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by babloo75 on 2011-01-03
sudo apt-get commands shows some options as 'Hit' and some others as 'Ign'.
What to do now?

---

### Post by babloo75 on 2011-01-05
I think this thread will remain unsolved, as this thread was started by me on my nephew's request. He has removed Kubuntu now and installed another Linux version.

Sincere thanks to all of you.

---

