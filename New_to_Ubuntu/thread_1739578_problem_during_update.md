---
title: "problem during update"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by hockguat on 2011-04-26
sorry i&#7743; totally new here, problem happened when updating.
E:Malformed line 67 in source list /etc/apt/sources.list (dist parse)'
what should i do. TQ

---

### Post by jtarin on 2011-04-26
Open up your /etc/apt/sources.list and correct line 67.
Did you make a new source entry?

---

### Post by hockguat on 2011-04-26
but how to open that..... 
yes i did install something just now totem pps

---

### Post by Pand5461 on 2011-04-26
First, make a backup of your file (just in case) by typing:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
```
in terminal. You will have a copy of the sources.list file in /etc/apt/sources.list.backup

Then just open the file as root in any text editor.
```
sudo gedit /etc/apt/sources.list
```

---

### Post by hockguat on 2011-04-26
can update now. thx.
but still cant install the ppa.launchpad
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  404  Not Found
Fetched 12.1kB in 7s (1,688B/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/cnav/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/cnav/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cnav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/cnav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by jtarin on 2011-04-26
Just as it says.....you have the wrong urls to the files. If you added ppa's to your sources you have added them incorrectly or they do not exist.

---

### Post by Pand5461 on 2011-04-26
It seems that PPA you're trying to use contains only packages for Natty and Lucid. Did you add it to software sources manually or using ppa-add-repository?

---

### Post by hockguat on 2011-04-26
just copy paste manually from forum...
so this mean that i got the wrong version....
do i have to uninstall or just leave it there...

---

### Post by Pand5461 on 2011-04-26
You don't have to uninstall the packages unless they are broken. It may occur that the PPA maintainers just left Maverick support recently. The only thing you have to do is uncheck/delete the PPA line in Software sources. You won't get updates of the packages from that PPA of course.
About adding PPAs: there is a convenient way to do this via ppa-add-repository.
> Step 1: On the PPA's overview page, look for the heading that reads Adding this PPA to your system. Make a note of the PPA's location, which looks like:

**ppa:gwibber-daily/ppa**

Step 2: Open a terminal and enter:

```
sudo add-apt-repository ppa:user/ppa-name
```

Replace **ppa:user/ppa-name** with the PPA's location that you noted above.
Your system will now fetch the PPA's key. This enables your Ubuntu system to verify that the packages in the PPA have not been interfered with since they were built.


Step 3: Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

```
sudo apt-get update
```

Now you're ready to start installing software from the PPA!

---

