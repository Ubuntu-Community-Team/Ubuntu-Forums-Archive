---
title: "Namoroka"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2010-04-13
I've been using Namoroka pretty much problem free since it was first released, however since about 2 days ago it has become very unstable.it just keeps freezing up when I refresh a page, change a page, open a new tab etc, and it's starting to really get on my nerves. From what I can gather, it has something to do with daily update something, but I can't find any way to turn that daily update thing off.
 
Does anyone know a simple way of getting Firefox back, or of any fixes that will make Namoroka run without freezing?

---

### Post by JDShu on 2010-04-13
hmmm, I would get rid of namaroka first

```
sudo apt-get purge firefox-3.6
```

and then make sure regular firefox is around

```
sudo apt-get install firefox
```

This is assuming you just installed Namaroka by doing sudo apt-get install firefox-3.6

---

### Post by T4K3Z0U on 2010-04-14
> **JDShu said:**
> 
This is assuming you just installed Namaroka by doing sudo apt-get install firefox-3.6

Thanks for the reply. I believe it was installed via update manager as I didn't know there was even a new release.

I will try those instructioons anyway to see what happens, but how can I prevent it updating again if I am successful in reinstalling Firefox?

ETA: I just tried those instructions and got this message.```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox-3.6 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

``` I assume that came up since I did not manually install Namoroka?

---

### Post by JDShu on 2010-04-14
This is quite odd, because Namaroka should not install unless the user manually does it. Maybe you somehow added one of the development firefox ppas? Check your software sources (System->Administration->Software Sources) and go to the "other software" tab. What shows up on that list?

Also I assume you're running 9.10?

---

### Post by T4K3Z0U on 2010-04-14
> **JDShu said:**
> This is quite odd, because Namaroka should not install unless the user manually does it. Maybe you somehow added one of the development firefox ppas? Check your software sources (System->Administration->Software Sources) and go to the "other software" tab. What shows up on that list?

Also I assume you're running 9.10?

I was surprised when it first showed up on my PC, I thought I had done something wrong, because it happened at the same time I accidentally hid my thunderbird folder when attempting to make a backup copy. I may have inadvertently downloaded it when trying to find info on what had happened to said folder before realizing it was only hidden and not deleted.

Moving on... In the "other software" tab there are a few things on the list, but only two which are checked. They are: Ubuntu 9.04 Jaunty Jackalope, and ppa launchpad for Mozilla. Perhaps I should uncheck that one?

Yes, I am using 9.10 and love it. Can't wait to see what they come up with next.

---

### Post by wojox on 2010-04-14
> **T4K3Z0U said:**
> 

Moving on... In the "other software" tab there are a few things on the list, but only two which are checked. They are: Ubuntu 9.04 Jaunty Jackalope, and ppa launchpad for Mozilla. Perhaps I should uncheck that one?


Yes uncheck or remove the mozilla ppa. You have the daily builds installed. Did you install TB3 that way? Have a look here for more help: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002")

---

### Post by T4K3Z0U on 2010-04-14
> **wojox said:**
> Did you install TB3 that way?

I attempted to install TB3 that way but think I was unsuccessful in the end.

---

### Post by wojox on 2010-04-14
> **T4K3Z0U said:**
> I attempted to install TB3 that way but think I was unsuccessful in the end.

Okay so it's not working either. Only reason I asked was because removing the daily build ppa's you wouldn't get updates for TB3. I would remove it only because I've seen a lot of people coming here lately with problems. I believe lovinglinux's page recommends ubuntzilla for grabbing the newest stable Firefox and TB3.

---

### Post by T4K3Z0U on 2010-04-14
I removed the PPA thing. Want to remove Firefox as well to try re-install it, but not sure which version I have since yesterday's attempt of purging told me 3.6 isn't installed. I didn't see any instruction of how to find version number.

---

### Post by wojox on 2010-04-14
> **T4K3Z0U said:**
> I removed the PPA thing. Want to remove Firefox as well to try re-install it, but not sure which version I have since yesterday's attempt of purging told me 3.6 isn't installed. I didn't see any instruction of how to find version number.

You could always run:

```
dpkg -s firefox
```

To see what you have.

---

### Post by T4K3Z0U on 2010-04-14
> **wojox said:**
> Okay so it's not working either. Only reason I asked was because removing the daily build ppa's you wouldn't get updates for TB3. I would remove it only because I've seen a lot of people coming here lately with problems. I believe lovinglinux's page recommends ubuntzilla for grabbing the newest stable Firefox and TB3.

Ubuntzilla is only for 32bit at the moment. I use 64bit. Not sure I need the latest version of firefox, the last one I had worked fine, as with TB.

---

### Post by T4K3Z0U on 2010-04-14
> **wojox said:**
> You could always run:

```
dpkg -s firefox
```

To see what you have.

Excellent, that worked. I apparently have 3.6.4 perhaps that's why purge didn't work because I only entered 3.6. Will try it again now, and if it don't work, I will use the instructions in the link you posted.

Thanks.

---

### Post by wojox on 2010-04-14
They do have a stable ppa for Firefox-3.6. This will download the 64 for you: [http://wojox.homelinux.net/?p=67](http://wojox.homelinux.net/?p=67)

---

### Post by T4K3Z0U on 2010-04-14
> Manual Installation and Removal 


Instead of using sudo checkinstall, you can simply use sudo make install for installing your compiled version of Firefox, but you won&#8217;t be able to remove it using Synaptic. To remove it manually, run the following commands:


sudo rm -f /usr/local/bin/firefox
sudo rm -fr /usr/local/lib/firefox-y.z.x
sudo rm -fr /usr/local/lib/firefox-devel-y.z.x
sudo rm -fr /usr/local/share/idl/firefox-y.z.x
sudo rm -fr /usr/local/include/firefox-y.z.x

Note:
Don&#8217;t forget to replace y.z.x and x.y.z with the corresponding firefox and mozilla versions.

These instructions don't appear to have worked for me. When I entered each code nothing happened, and the terminal page has the code displayed just as it is here (with py username preceding it).

---

### Post by T4K3Z0U on 2010-04-14
> **wojox said:**
> They do have a stable ppa for Firefox-3.6. This will download the 64 for you: [http://wojox.homelinux.net/?p=67](http://wojox.homelinux.net/?p=67)

I used those commands even though I hadn't (or don't think I had) removed FF. Is this going to prevent FF from crashing on me?

ETA: It still crashes. Will go through and read more from that first link you gave, and see if I can get it fixed.

Thanks again.

---

### Post by T4K3Z0U on 2010-04-16
Perhaps I am doing something wrong, I still can't get it to stop crashing. I will try again to remove it then reinstall firefox, assuming I'm not automatically given the same new version.

---

### Post by wojox on 2010-04-16
Maybe you should uninstall any ppa's and look here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by T4K3Z0U on 2010-04-16
> **wojox said:**
> Maybe you should uninstall any ppa's and look here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

I removed the only PPA, and I tried removing FF with the instructions on that page but didn't work. Also tried some flash optimization to no avail.

Also tried removal via software center, that too was unsuccessful.

---

### Post by T4K3Z0U on 2010-04-16
I found another terminal command for removing 3.6, it spat out this report which says it removed 3,6. ```
sudo apt-get purge firefox-3.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-3.6*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 28.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 325208 files and directories currently installed.)
Removing firefox-3.6 ...

```

Only problem is, 3.6 is still there...:confused:

---

### Post by T4K3Z0U on 2010-04-17
So after getting more peeved with this new browser, and trying to remove it, but being told it isn't installed, I tried a different approach, Rather than trying to purge firefox 3.6, I decided to try purge firefox, it worked. Then I installed firefox again, and that too worked. Only trouble is my fan seems to be in overdrive.

Main thing is Namoroka is gone, FF is back, and I'm happy again until the next drama.

---

### Post by wojox on 2010-04-17
I take it the fan problem wasen't an issue before you purged Firefox ?

---

