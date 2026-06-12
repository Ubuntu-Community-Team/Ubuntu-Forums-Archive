---
title: "sources.list - query on modifying"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by chomeop on 2008-12-30
Hi all.

I've just installed mythbuntu and i'm trying to setup the Australian archive mirror in the /etc/apt/sources.list

all i have is the URL of my ISP mirror.

[http://mirror.exetel.com.au/pub/ubuntu/ubuntu/dists/intrepid/](http://mirror.exetel.com.au/pub/ubuntu/ubuntu/dists/intrepid/)

how do i turn this into something i can add into the file so i can grab the updates at a decent speed?

many thanks!

Edit:
probably worth noting i'm running the AMD 64 version

---

### Post by drs305 on 2008-12-30
Here are the ubuntu wiki links to adding repositories to ubuntu. The first is for gui, the second for CLI:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab")
 
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

I have done a bit of searching and found many people had problems with the exetel mirrors.

---

### Post by drs305 on 2008-12-30
I played with this and the format is a bit non-standard. While I still encourage you to review the information in the links in the preceding post, this is the entry you would add command line to include the exetel libraries to your sources.list. Of course, you can also add the repository manually through either Administration > Software Sources or Synaptic > Repositories > Third-Party Software. 

This is for intrepid, first backing up sources.list and then to add the exetel repositories, including main, universe, multiverse and restricted:

Open a root shell, backup sources.list, and add the entry to sources.list via command line:
```

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.backup
echo 'deb http://mirror.exetel.com.au/pub/ubuntu/ubuntu intrepid main multiverse universe restricted' >> /etc/apt/sources.list
apt-get update

```
Close the terminal.

---

### Post by a7ndrew on 2009-01-30
The Iprimus mirror [http://mirror.iprimus.com.au/ubuntu/](http://mirror.iprimus.com.au/ubuntu/) seems to work for me. Should be free for Iprimus customers.

---

### Post by buffy^ on 2009-01-30
If you were interested in the scources list to see whats in there try
```

nano /etc/apt/sources.list
```

If you want to edit it

```
sudo nano /etc/apt/sources.list
```

That way you can get a better understanding of what it is that you are looking it.

---

