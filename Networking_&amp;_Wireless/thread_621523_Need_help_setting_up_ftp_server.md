---
title: "Need help setting up ftp server"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by mhorn1003 on 2007-11-23
Hello, everyone.
I am a recent Windows convert trying to get familiar with this Linux thing.  I hosted a small ftp server on my windows box and I am trying to replicate it here so that I never have to go back.  On my windows machine a ran a Filezilla FTP server and used No-IP to attach my domain name to my dynamic address.

I have been reading a little bit about it via Google search and so far it is all Greek to me.  I am aware that the No-IP service supports Linux, but I haven't yet mastered the terminal commands..

What I am looking for are some graphical interfaces for both an ftp server and the No-IP client software, like I had in windows.  Does anyone know of any options.  Or, can anyone dumb down a tutorial to help a noob?

---

### Post by groovomata on 2007-11-27
Hey, I'm trying to set up an ftpserver on my ubuntu 7.10 box as well and I found an article. This may be of help. It include both a server and a client. I haven't gone through it yet but I'm going to give it a try now. I'll post back and let you know of my success or failure!
[http://www.ubuntugeek.com/how-to-setup-file-sharingsftp-for-machines-by-newbie-in-5-minutes.html](http://www.ubuntugeek.com/how-to-setup-file-sharingsftp-for-machines-by-newbie-in-5-minutes.html)
Erik.
p.s. I also found this page as well:
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by mhorn1003 on 2007-11-28
Thanks.  I'll look into it.  Do you happen to know if the No-IP service has a GUI for Linux systems?

---

### Post by EspressoRulz on 2007-11-28
I have used proftpd with gproftpd as the GUI front end.  You can take a look at gproftpd here -->  [http://freshmeat.net/projects/gproftpd/](http://freshmeat.net/projects/gproftpd/)

Both are available in the Ubuntu repository.

---

### Post by groovomata on 2007-12-02
I was able to successfully transfer files to a windows computer using the crossftp server. It is cross platform as it runs on windows as well. I was able to transfer files using the crossftp client and also fireftp (the firefox ftp extension). 
The link is here: [http://www.ubuntugeek.com/how-to-set...5-minutes.html](http://www.ubuntugeek.com/how-to-set...5-minutes.html)
One thing I noticed is that I had to play with the settings to get it to work. With foxftp I had to unselect 'passive mode. With the crossftp client, I had to use the 'Port Connection Mode'. 
So I was successfully able to get it to work.
Erik.

---

