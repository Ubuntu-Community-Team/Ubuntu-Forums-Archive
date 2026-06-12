---
title: "Make a local repository mirror"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by scribebox on 2008-05-04
Here is my situation, i have a windows server 2003 box in my home, hooked up over a 3mb DSL line, with 4 500GB harddrives (2ntfs basic, 2 ntfs dynamic) no raid0/1 or anything like that, just 4 500GB harddrives.  ive been using ubuntu on all my desktop / laptop systems (4 total), and im constantly needing to connect to the internet, to download packages for different things, which isnt a problem, until a month from now, when i move, im moving to the country, where ill only have access to dialup, so id like to download all the current repositorys and setup a local mirror at my house (universe / standard / multiverse).  setting it up on the windows 2003 box would be good, id even convert the windows 2003 box to ubuntu, if i had some assurance that my 2 ntfs dynamic, and my 2 ntfs basic disks, would run fine :)  (note: i have a blank 30GB partition, that would work fine for an ubuntu install).

anyway, any help setting this up, would be appreciatted.

i would also need an easy way to make sure the mirrors were current, so if i ever toted my box into town, hooked up to my brothers dsl line, i could easily update my repositorys to the most current.

thanks

-Dustin

---

### Post by nixscripter on 2008-05-05
To answer your second question first: linux does not have very good support for NTFS. It is generally read-only; you can only write if the new data is exactly the same size as the old data. Your 2 TB (that's a lot!) of stuff would probably require another filesystem, such as XFS, if you were to move it to linux.

Even assuming you have the space for it, however, I don't think you would need to set up a mirror just for package updates. Instead, I would suggest just saving all of the package files when you get them, and then copying them over to the other computers when they need to update too.

To do this, on the computers, open the Synaptic Package Manger, and go to Settings-> Preferences->files. Check "leave all downloaded files in the package cache". Then, whenever you update stuff, you can just find the file (use the **apt-cache** utility), copy it to the other machines, and "Add Downloaded Package" in their package managers.

It's somewhat awkward, but I think it's a lot simpler than trying to maintain a mirror. I hope it helps anyway.

---

### Post by ytene on 2008-05-05
I have a similar challenge... except I have a single hardware platform with multiple ubuntu images that boot from it. This is achieved by using SATA drives in removable caddy units. Each caddy contains a disc with a bootable ubuntu configuration, but on a second "internal" drive I have 4 partitions that can be made visible to any OS that boots in the machine.

All I do is very simple...

1. Put the apt cache on one of the shared discs. Something like this:

cd /var/cache

cp -r apt /media/sdc2/shared/var/cache/apt/

mv apt apt_orig

ln -s /media/sdc2/shared/var/cache/apt apt


OK then... Quick explanation. You cd into the cache directory. The cp command recursively copies the entire contents of the apt sub-directory to a new destination of your choice. Make it anywhere that all your machines can see it. Now rename your existing apt directory with the move command [mv] to keep a copy safe while you're experimenting.

Finally, create a soft-link to the relocated apt cache where your local machine would expect to see it. 

You still have to do the downloads at least once [hey, that's life] but once they are there, any subsequent machine I boot from this configuration can check the net for update packages, then magically "find" them in it's cache. There's never a need to download anything more than once. 



If you wanted to get really technical, there are other things you could do. For example, on your one machine that connects to the internet to download packages, start an ftp daemon like proftp. Then, on your other machines, you could actually rsync with your localised ftp server on a cron basis [or on demand] so that you keep all your machines up to the same patch level. 



There are probably several other ways that you could achieve this, all of which would be valid for you. If you have a laptop or other mobile hdd capability and have an opportunity to visit somewhere with a faster connection, then you can even bring in images with a mobile machine and synchronise locally. 

In all of these cases I'm suggesting that you'd want your machines to see the ubuntu master servers to be aware of the packages that are being released, but I suppose you don't even need to do that if you don't want to. Simply cd into the appropriate storage directory and issue the necessary apt-get command with '*' on the end, and it should try and install everything there, bringing in just the new updates as it goes.

---

### Post by Chayak on 2008-05-06
It's easy

```
sudo apt-get install debmiror
```

create a text file with the name repoupdate.sh and copy the following

```
#############################
#!/bin/bash -x
# Start of the repo update script

/usr/bin/debmirror --nosource -m --passive --host=us.archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --ignore-release-gpg --dist=hardy --section=main,multiverse,universe,restricted --arch=i386 /repo/ubuntu/
#NOTE: the /repo/ubuntu is the location the repository will be copied to change the last bit to suit your needs
#NOTE: change the --dist=  to whatever distro you need
#############################
```

save and then set the repoupdate.sh as executable which can be done in the properties tag.  The /usr/bin/debmirror and the rest should all be on one line so make sure there are no line returns cause by cut and paste.

sudo and run the script and it will create a local repo mirror at the location you gave it in the script "/repo/ubuntu" for my system.  You can add the script to a cron job to update as you wish

```
open your /etc/apt/sources.list and add

deb file:///<path to the repo> hardy main universe multiverse restricted
```

You now have a local repository for that machine
The alternative is to use rsync but debmirror works.

To use it from another machine on your LAN make a symbolic link in the web server directory to your repo folder

Install apache if you don't have it already

```
cd /var/www/
sudo ln -s <path to repo> repos
```

Modify the privs of the repo folder

```
chmod 770 <repo dir>
```

Test it by opening it from localhost ex. http://localhost/<repo path> 
If it works it's time to modify your sources.list again

```
sudo gedit /etc/apt/sources.list

deb http://<machine ip or name>/<repo path> hardy main universe multiverse restricted
```

---

### Post by znotdead on 2008-11-24
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror) &#1074;&#1077;&#1089;&#1100;&#1084;&#1072; &#1079;&#1072;&#1084;&#1077;&#1095;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086; &#1086;&#1087;&#1080;&#1089;&#1072;&#1085; &#1077;&#1077;&#1097; &#1086;&#1076;&#1080;&#1085; &#1074;&#1072;&#1088;&#1080;&#1072;&#1085;&#1090;&#1089; &#1087;&#1086;&#1084;&#1086;&#1097;&#1100;&#1102; apt-mirror. &#1088;&#1077;&#1082;&#1086;&#1084;&#1077;&#1085;&#1076;&#1091;&#1102; &#1087;&#1088;&#1086;&#1095;&#1080;&#1090;&#1072;&#1090;&#1100; )

---

