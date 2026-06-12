---
title: "I have messed up  my synaptic package manager"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Umptyscratch on 2011-07-05
I was trying to add some repositories following instructions from the net however it didnt work and now my programs loads gets an error and closes.

I have used a source list builder and changed it but still not luck but this seems to be a file not located in the sources.lst anyways. Here is the error I get :
E: Type '/brianmercer/php/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/brianmercer-php-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I ran  sudo rm /etc/apt/sources.list.d/brianmercer-php-natty.list as I had read somewhere to do that still get the same error.


my source.lst is this:



#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Deluge BitTorrent - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main 


####### 3rd Party Source Repos

#### Deluge BitTorrent (Source) - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main


thanks for any help not sure what else to do!!

---

### Post by alphacrucis2 on 2011-07-05
> **Umptyscratch said:**
> I was trying to add some repositories following instructions from the net however it didnt work and now my programs loads gets an error and closes.

I have used a source list builder and changed it but still not luck but this seems to be a file not located in the sources.lst anyways. Here is the error I get :
E: Type '/brianmercer/php/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/brianmercer-php-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I ran  sudo rm /etc/apt/sources.list.d/brianmercer-php-natty.list as I had read somewhere to do that still get the same error.


my source.lst is this:



#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Deluge BitTorrent - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main 


####### 3rd Party Source Repos

#### Deluge BitTorrent (Source) - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main


thanks for any help not sure what else to do!!

The problem isn't the /etc/apt/sources.list 

The problem is the file:

/etc/apt/sources.list.d/brianmercer-php-natty.list

Note that sources.list.d is a directory. When you run apt-add-repository it creates a <repo name>.list file under /etc/apt/sources.list.[COLOR="Red"]d[/COLOR]/

Browse to the folder under nautilus and verify that you really did delete the file. or cd /etc/apt/sources.list.d and then do an ls -l to see exactly what is there.

---

### Post by wildmanne39 on 2011-07-05
Hi, I think these two command will also fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Paqman on 2011-07-05
> **Umptyscratch said:**
> I was trying to add some repositories following instructions from the net however it didnt work and now my programs loads gets an error and closes.


Assuming you've now fixed your problem, can you give us the link to the instructions you were following and tell us what you were trying to do?

Generally editing sources.list by hand is a bad idea, and I wouldn't use a 3rd party tool to edit it either. You can add extra repos either on the command line (many repos will give you commands to do this) or in the Software Sources tool.

---

### Post by Umptyscratch on 2011-07-05
> **Paqman said:**
> Assuming you've now fixed your problem, can you give us the link to the instructions you were following and tell us what you were trying to do?

Generally editing sources.list by hand is a bad idea, and I wouldn't use a 3rd party tool to edit it either. You can add extra repos either on the command line (many repos will give you commands to do this) or in the Software Sources tool.

I ran the commands wildmann posted and that fixed it. Thats the first time I have encounter the .d so at least now I know its a directory. When all this happened I was following a page that I found which was a 10 or something things to do after you upgrade your ubuntu and it recommended adding a few repositories so I tried to do .. it was all done via gui or command line. My computer I have this one was down for a bit as I had to move it when I got back I was looking for a torrent and the manager wouldnt load.  I know the list had me add something that was suppose to turn on something that was defaulted off with the upgrade in software center I am thinking.  I wanted to add more repositories figuring I could find more programs that I would like but not too worried about it now. I know whatever I did to add the repository I had to get and add a key too ..Wish I could remember the webpage but been through a lot of different pages so I dont.  Thanks everyone for the help !!

---

### Post by wildmanne39 on 2011-07-05
> **Umptyscratch said:**
> I ran the commands wildmann posted and that fixed it. Thats the first time I have encounter the .d so at least now I know its a directory. When all this happened I was following a page that I found which was a 10 or something things to do after you upgrade your ubuntu and it recommended adding a few repositories so I tried to do .. it was all done via gui or command line. My computer I have this one was down for a bit as I had to move it when I got back I was looking for a torrent and the manager wouldnt load.  I know the list had me add something that was suppose to turn on something that was defaulted off with the upgrade in software center I am thinking.  I wanted to add more repositories figuring I could find more programs that I would like but not too worried about it now. I know whatever I did to add the repository I had to get and add a key too ..Wish I could remember the webpage but been through a lot of different pages so I dont.  Thanks everyone for the help !!
Hi, your welcome, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

