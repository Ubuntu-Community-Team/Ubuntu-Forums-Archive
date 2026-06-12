---
title: "SBAnzbd"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by shadowlands on 2009-06-05
there is a guide at [www.sabnzbd.org](www.sabnzbd.org) 
The forum is really  good also step by step directions from folk.  They seem to take things as you are new so they help step by step.  Members tell you the correct words to use so you are searching for things with the correct search terms.  I like the links they have to the wikis and such for the terms!! That helps a lot. They tend to remember that alot of end users are switching over to use stuff and end users and computer minded peopel think a lot differently!!
I hopw this helps someone else. 

To install SABnzbd: These are the commands that go in to the terminal. 

sudo apt-get install sabnzbdplus
sudo apt-get install sabnzbdplus-theme-smpl
sudo apt-get install sabnzbdplus-theme-iphone
sudo apt-get install sabnzbdplus-theme-plush

After everything's installed

run this command
sabnzbdplus

And you can use the web interface to set everything up.

---

### Post by shadowlands on 2009-06-05
Ok, what you need to do is start up SABnzbd, then click on the config button, then go through each tab. One of the tabs will be server settings, this is where you need to set up your server information

news.giganews.com
port:119
user name: 'your user name'
password: 'you password'
connections: 10
SSL: No
Fill server: No

Click on the save button, and you should be good to go.

There's a folder tab, and you will need to set up where you want SABnzbd look for /nzb files. If you are using firefox, then I would have it go to Desktop
and place completed files in to Videos

Thanks for helping me and providing me with this info!!!!


**mangurt**ROCKS!!!!!!!!

---

### Post by shadowlands on 2009-06-05
There seems to be some type of plug in that goes with foxfire that acts as the interface. There seeme to be a problem with the API keys and it is also being reported by folk other than me that they are having a problem. with missing API Keys.  Can someone help please?

---

### Post by shadowlands on 2009-06-06
I think I got it.  The password that I needed to put into the third party config  had to be the same user name and pass word that was set up in order to open SAB.... This connects the two together.  When I did this step, the warning about missing API key for the interface stopped.


Now the question is how do I use the program I installed? Well back to google. If anyone has an easy to follow guide or know of any search terms I might need to use to pull up the correct info please feel free to post it here.

---

### Post by Staach on 2009-08-31
I got this wierd problem. I have setup a xubuntu as webserver and wanted to top it with sabnzbd+. I installed it, tested it and everything was fine (had to change "localhost" to 0.0.0.0 to reach the webpage from other hosts though). Then I placed the server where it should be, logged on via ssh and could only start sabnzbd+ by using sudo!? Not really a problem I thought, but suddenly the downloaded folders (and all files in them) don't have me as owner - in fact it looks like they don't have an owner at all. I can only reach them as root, which is not easy when trying to access them from windows installations on the LAN.

Can any one help me on this?

---

### Post by nhasian on 2009-08-31
> **shadowlands said:**
> there is a guide at [www.sabnzbd.org](www.sabnzbd.org)

To install SABnzbd: These are the commands that go in to the terminal. 

sudo apt-get install sabnzbdplus
sudo apt-get install sabnzbdplus-theme-smpl
sudo apt-get install sabnzbdplus-theme-iphone
sudo apt-get install sabnzbdplus-theme-plush


did you know you could install multiple packages at the same time?

```
sudo apt-get install sabnzbdplus sabnzbdplus-theme-smpl sabnzbdplus-theme-iphone sabnzbdplus-theme-plush
```

How does it compare to hellanzb?

> **Staach said:**
> ...start sabnzbd+ by using sudo!? Not really a problem I thought, but suddenly the downloaded folders (and all files in them) don't have me as owner

Staach, dont run it as sudo.

---

### Post by Staach on 2009-08-31
> Staach, dont run it as sudo.
Well, that's the problem..I can't seem to start it unless I use sudo..Any ideas on how to start it without sudo? Just typing sabnzbdplus doesnt make it start (tried sabnzbdplus -d but same outcome). I get an error about it not having permition to open socket.

---

### Post by mangurt on 2009-08-31
Here's a small suggestion, why don't you try hellanzb instead of SABnzbd on the server?  Hellanzb is in the repo.  It does not have the GUI (it's commandline based).  You can change all your settings in the config file (/home/user/ect/hellanzb.conf)
You can have that running in the back ground, and dump your nzb files into the watched folder on your server....

---

### Post by Staach on 2009-08-31
What really makes Sabnzbdplus so cool, is that it automatically checks newzbin for any new bookmarks and then starts downloading them.. I don't think Hellanzb can do that? 
I believe I must have F***** up somewhere while playing around with sabnzbd+..so, now I just need to get it back to normal..Guess the easy way out would be to uninstall it and then install it once more - unless any one has an idea to why my "normal" user don't have the needed permissions..

---

### Post by shadowlands on 2009-09-18
the login page comes up but there is no place to reg. a password or user name.

---

