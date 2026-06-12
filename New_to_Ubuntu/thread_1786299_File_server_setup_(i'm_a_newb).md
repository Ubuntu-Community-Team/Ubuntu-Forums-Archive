---
title: "File server setup (i'm a newb)"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by curly57_ on 2011-06-19
Hi, i'm new to the forum, and i have absolutely no idea about any version of linux. I've pretty much always used windows, though i have always been intrigued by linux and it's many different forms.
 
I have a server that i run at home. I want it to be a fileserver, so that all files can be accessed from a central souce at home, things like films and music mostly, but also programs and applications etc. it's basically be a huge dump. It mainly runs an FTP and my website (just a private family thing) no more than 3 or 4 people will view the site or use the FTP.
 
I have it running on a 'borrowed' copy of server 2k3 as a test mule, and to be honest, it's just too slow, or a pain in the backside.
 
I know a lot of people use linux based servers, so i though i'd have a look at it and see if it will be a better platform for what i need.
 
So, what i need from it is...
 
1. File server. 
2. Media server (mostly for sharing films to my kids ps3)
3. Web accessible FTP server.
4. Web accessible website.
5. It needs to be able to run Vuze/torrent download upload program.
6. It needs to be able to run Teamspeak 3 server.
7. VNC (or similiar) would be usefull too so that i don't have to keep going to the server to change things or check on it.
8. It needs to be compatible with all versions of windows from XP onwards.
 
It doesn't need to be a DHCP or a domain controller for the network, my router does the DHCP bit already.
 
I already have a registered domain name that is pointing to my home IP, and it works ok (though it's a little limited by my up speed, but that should change soon).
 
The machine itself is:-
 
Athlon X2 255 @ 3.11ghz
2GB of ddr3 @667mhz
onboard sound and graphics (it doesn't run anything other than the above, sound isn't required for teamspeak as it is just a silent user).
Approx 1.7tb of disc space, Main windows drive is 250gb.
 
 
More memory is going to be added at some point, but it runs ok for now. 
 
So, going from the above, is Linux/ubuntu going to be a good operating system to run instead of windows server? Will i be able to use all of the above?
 
And lastly, how hard will it be for someone who hasn't seen dos since the dark ages, to setup, secure and run the above. 
 
Let me put it this way, in terms of knowing how to use linux, i'm so green, i'd glow in the dark :P.
 
Any help, advice and suggestions would be apreciated greatly.
 
Thanks in advance,
 
Gav.

---

### Post by mmad on 2011-06-19
> **curly57_ said:**
> Hi, i'm new to the forum, and i have absolutely no idea about any version of linux. I've pretty much always used windows, though i have always been intrigued by linux and it's many different forms.
 
I have a server that i run at home. I want it to be a fileserver, so that all files can be accessed from a central souce at home, things like films and music mostly, but also programs and applications etc. it's basically be a huge dump. It mainly runs an FTP and my website (just a private family thing) no more than 3 or 4 people will view the site or use the FTP.
 
I have it running on a 'borrowed' copy of server 2k3 as a test mule, and to be honest, it's just too slow, or a pain in the backside.
 
I know a lot of people use linux based servers, so i though i'd have a look at it and see if it will be a better platform for what i need.
 
So, what i need from it is...
 
1. File server. 
[COLOR="Red"]No problem - SAMBA deals with this[/COLOR]
2. Media server (mostly for sharing films to my kids ps3)
[COLOR="Red"]No problem - PS3 Media Server[/COLOR]
3. Web accessible FTP server.
[COLOR="Red"]Havent done this myself, but again I doubt its a problem[/COLOR]
4. Web accessible website.
[COLOR="Red"]Standard server install will allow you to install Apache[/COLOR]
5. It needs to be able to run Vuze/torrent download upload program.
[COLOR="Red"]Torrentflux[/COLOR]
6. It needs to be able to run Teamspeak 3 server.
[COLOR="Red"]Haven't done this, but a quick google search indicates that this shouldnt be an issue[/COLOR]
7. VNC (or similiar) would be usefull too so that i don't have to keep going to the server to change things or check on it.
[COLOR="Red"]I VNC into my server all the time (I have a GUI installed) but you can ssh into it aswell for quick administration if you want.[/COLOR]
8. It needs to be compatible with all versions of windows from XP onwards.
[COLOR="Red"]Samba will handle this[/COLOR]
 
It doesn't need to be a DHCP or a domain controller for the network, my router does the DHCP bit already.
 
I already have a registered domain name that is pointing to my home IP, and it works ok (though it's a little limited by my up speed, but that should change soon).
 
The machine itself is:-
 
Athlon X2 255 @ 3.11ghz
2GB of ddr3 @667mhz
onboard sound and graphics (it doesn't run anything other than the above, sound isn't required for teamspeak as it is just a silent user).
Approx 1.7tb of disc space, Main windows drive is 250gb.
 
 
More memory is going to be added at some point, but it runs ok for now. 
 
So, going from the above, is Linux/ubuntu going to be a good operating system to run instead of windows server? Will i be able to use all of the above?
[COLOR="Red"]Way more than necessary - nothing to worry about :D[/COLOR]
 
And lastly, how hard will it be for someone who hasn't seen dos since the dark ages, to setup, secure and run the above. 
[COLOR="Red"]Took me about 30 minutes of research, and 1 hour setup time - It was the first time I set up the server aswell[/COLOR]
 
Let me put it this way, in terms of knowing how to use linux, i'm so green, i'd glow in the dark :P.
 
Any help, advice and suggestions would be apreciated greatly.
 
Thanks in advance,
 
Gav.

All you need is the basic server install, then the installation of the other applications - a quick search will show you the possibilities! You'll be up and running in no time.

---

### Post by kaldor on 2011-06-19
I agree with the above poster. Don't be afraid to get your hands a bit dirty, but it shouldn't be too hard at all. I believe any flavour of Linux is infinitely better than Windows when it comes to stuff like this. Unless you need Microsoft-specific server software such as Exchange or AD, then Windows serves no real purpose on the server side. Since your box will be accessible to the world (Web hosting and FTP) then you're going to want security and uptime. You can use the Ubuntu Server Edition to start out, but if you feel you need a GUI, then you can easily add that.

It was a pretty quick job for me to set up my own home file server for personal use. I was amazed when it took me only a few minutes to get it up and running for what I wanted to do. Granted, this is much more advanced than what I needed, but there's a huge wealth of information available for this. 

Here are a couple of links to check out..

[FTP Server]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html") 

[Apache Web Server]("http://www.easy-ubuntu-linux.com/apache-ubuntu-install.html")

Good luck :)

---

### Post by metalf8801 on 2011-06-19
Yes you can do all of that with Ubuntu but you most likely don't want any home server accessible from outside of your home network both for security reasons and because your probably going to violate your Internet Security Provider terms of service. 

There are 2 versions of Ubuntu that you might want to use since your looking for a server you most likely want Ubuntu 10.04 LTS because the server version will be supported until 2015.
Then there is the latest version of Ubuntu which is 11.04 which will have newer packages in its repository but it will only be supported untill 2013. When the support for a server OS ends your have to upgrade to a new version or you could have major security problems because you are not getting the latest security patches.


1. File server and 8. It needs to be compatible with all versions of windows from XP onwards.
Using **Samba** you can setup a Ubuntu file server that will work with all versions Windows XP and above [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html) or 

2. Media server (mostly for sharing films to my kids ps3)
**Mediatomb** is a media server that can be setup to work with the PS3 [http://mediatomb.cc/pages/documentation](http://mediatomb.cc/pages/documentation)

3. Web accessible FTP server.
Can be done but don't make it accessible from outside of your home network 

4. Web accessible website.
Can be done but again major security risk but if your going to do it you can use Apache [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html) which is the words more popular web server or you might consider the Cherokee web server [http://www.cherokee-project.com/](http://www.cherokee-project.com/) which is going to be a little easer to use because it uses a Webgui/web-interface to configure it instead of the command line.   

5. It needs to be able to run Vuze/torrent download upload program.
There are server side programs to download and seed all kinds of legal torrents

6. It needs to be able to run Teamspeak 3 server.
Teamspeak server version 2.0.24 is in the Ubuntu repository but it looks like you can Teamspeak server version 3 for Linux on the Teamspeak website. [http://www.teamspeak.com/?page=downloads](http://www.teamspeak.com/?page=downloads)

7. VNC (or similiar) would be usefull too so that i don't have to keep going to the server to change things or check on it.
you can use VNC or Freenx [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) as remote desktop or you can go with a WebGUI like Webmin [http://ubuntuforums.org/showthread.php?t=1686705&highlight=webmin](http://ubuntuforums.org/showthread.php?t=1686705&highlight=webmin) [http://www.webmin.com/](http://www.webmin.com/) or eBox if you want to use ebox I recomend using Zentyal which is a Linux distribution based on Ubuntu 10.04 with ebox setup [http://www.zentyal.org/](http://www.zentyal.org/)

While you can do all of this stuff with Ubuntu and there are good reasons to use Ubuntu like the great forum support for new users and that because Ubuntu is popular applications are more likely to work properly on it than a more obscure distribution

However you might want a Linux distribution that is specifically designed to be used as a home server like SalineOS PSE [http://www.salineos.com/personalserver.php](http://www.salineos.com/personalserver.php) 

The Amahi project might be another options [http://www.amahi.org/](http://www.amahi.org/) its not really its own distribution but the idea is to make an easy to use home server

I hope this helps and good luck 
Dan

---

### Post by drdos2006 on 2011-06-19
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

