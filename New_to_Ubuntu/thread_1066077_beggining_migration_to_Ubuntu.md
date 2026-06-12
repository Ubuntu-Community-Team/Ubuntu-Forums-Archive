---
title: "beggining migration to Ubuntu"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jabbadahutt762 on 2009-02-10
just downloaded the ISO for 8.10 i believe it was and burned onto a CD and installed.  have a few questions to ensure my system is properly configured.  first of all, i was amazed at how quick and easy this OS installed.  ive tried linux in the past and always ended back up with windows.  i think this time it may stick with me.

im going to be using this machine very basically as an HTML server.  that being said, i need the Apache module or similar and an FTP server module.  i dont recall exactly how the get command works.

secondly, the machine im running this on has dual pentium 4 CPU's.  how do i go about making sure that the OS sees both processors and handles the load effectively?  does the standard ISO that i downloaded seek out and install whats needed for that already?

lastly, video and sound are really not a concern to me as i will most likely be administering this machine over the LAN.


most of this is older hardware i had laying around so i dont recall the specifics but i can provide at a later time if needed.

thanks anyone for your help with this, i really am an above average PC user but linux for whatever reason has always eluded me but im a pretty fast learner.

---

### Post by billgoldberg on 2009-02-10
> **jabbadahutt762 said:**
> just downloaded the ISO for 8.10 i believe it was and burned onto a CD and installed.  have a few questions to ensure my system is properly configured.  first of all, i was amazed at how quick and easy this OS installed.  ive tried linux in the past and always ended back up with windows.  i think this time it may stick with me.

im going to be using this machine very basically as an HTML server.  that being said, i need the Apache module or similar and an FTP server module.  i dont recall exactly how the get command works.

secondly, the machine im running this on has dual pentium 4 CPU's.  how do i go about making sure that the OS sees both processors and handles the load effectively?  does the standard ISO that i downloaded seek out and install whats needed for that already?

lastly, video and sound are really not a concern to me as i will most likely be administering this machine over the LAN.

most of this is older hardware i had laying around so i dont recall the specifics but i can provide at a later time if needed.

thanks anyone for your help with this, i really am an above average PC user but linux for whatever reason has always eluded me but im a pretty fast learner.

Yes the cores will all be used, no problem there.

If you want Apache, install the lamp package. (google install lamp on ubuntu for guides)

For the ftp server:

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by Temposs on 2009-02-10
I'm glad you've had a good experience with Ubuntu so far. Installing software can be done 3 main ways.

For user-level software applications, you can use the Add/Remove GUI in the Applications menu.

For searching and installing every package through a GUI, the Synaptic Package Manager is used. Access through System->Administration

Through command line, you use something like:

```
sudo apt-get install package-name
```

where 'package-name' is the name of the package you'd like to install. Check:

```
apt-get --help
``` for a list of the other things you can do with apt-get, like for uninstalling stuff and updating stuff.

In general, try to use these three methods as much as possible, and avoid downloading other versions of software from the web(like you would do in Windows) unless it is critical for your needs. This will keep Ubuntu the most stable it can be.

---

### Post by jabbadahutt762 on 2009-02-10
> **Temposs said:**
> I'm glad you've had a good experience with Ubuntu so far. Installing software can be done 3 main ways.

For user-level software applications, you can use the Add/Remove GUI in the Applications menu.

For searching and installing every package through a GUI, the Synaptic Package Manager is used. Access through System->Administration

Through command line, you use something like:

```
sudo apt-get install package-name
```

where 'package-name' is the name of the package you'd like to install. Check:

```
apt-get --help
``` for a list of the other things you can do with apt-get, like for uninstalling stuff and updating stuff.

In general, try to use these three methods as much as possible, and avoid downloading other versions of software from the web(like you would do in Windows) unless it is critical for your needs. This will keep Ubuntu the most stable it can be.

oh man, that is exactly what i was looking for!!  thank you for your help!  i also just downloaded the pocket guide and im getting ready to spool it to my printer here at the office.  not much of a reader but i surely like to have reference material readily available.  hopefully when im ready to roll out the modules on the http server it will help.

i seriously was expecting to get horribly flamed in this thread for my ignorance.  thanks for your patience!

---

### Post by jabbadahutt762 on 2009-02-10
> **billgoldberg said:**
> Yes the cores will all be used, no problem there.

If you want Apache, install the lamp package. (google install lamp on ubuntu for guides)

For the ftp server:

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

excellent info!  thanks!

---

### Post by Temposs on 2009-02-10
There are lots of folks posting to this forum in a lot worse shape than you in terms of computer knowledge.

I think marking this forum section 'Absolute Beginner Talk', flaming is kept to a minimum, and an atmosphere of safety and helpfulness is generally fostered pretty well here, I think.

Good luck!

---

### Post by jabbadahutt762 on 2009-02-10
> **Temposs said:**
> There are lots of folks posting to this forum in a lot worse shape than you in terms of computer knowledge.

I think marking this forum section 'Absolute Beginner Talk', flaming is kept to a minimum, and an atmosphere of safety and helpfulness is generally fostered pretty well here, I think.

Good luck!

so far ive noticed.  too used to surfing the star wars forums i guess.  i felt a tingle when i clicked the submit button a bit ago.

---

### Post by JK3mp on 2009-02-10
Glad to hear your having good experience! Good Luck! :D

---

### Post by jabbadahutt762 on 2009-02-10
> **JK3mp said:**
> Glad to hear your having good experience! Good Luck! :D

thanks, if all goes well, i might convert all my boxes over.  
wonder how it would work on my gaming/media box?  been using a that VLC player for years through windows which is based off a linux program from what i understand.  any idea what software supports blue ray players?  not sure if the VLC does, if memory serves i had to install a stand alone program for just that within windows.  especially since ive never actually purchased windows and i can only download select updates as a result of that.  excluding WMP 10 and IE7 for instance.

---

### Post by jabbadahutt762 on 2009-02-11
well as an update to my ongoing saga, last night i thought id try to experiment with getting the LAN up and running and trying to get access to my windows network devices.  to my suprise, the LAN cable was plugged in and within seconds, DHCP kicked in and auto configured the whole deal!  i was surfing the net within seconds.  

my next project was to start using the get app within the gui.  i was trying to find the VLC player because im very familiar with it and i really like it over all other media players ive found.

i got a bit stuck at this point.  the search function was not finding it as suggested on the videolan website.  i thought that perhaps i should check for updates and see where that path took me.  noticed an icon in top right corner proudly letting me know that 142 updates were available.  not sure if i should have but i went ahead and downloaded all of them and allowed them to install.  i figure worst case ill just go through and remove whatever i dont need later on.  at that point i shut off the monitor and hit the sack and let it go about its business.  this morning i saw that it required a system restart.  went ahead and did that and stood around a moment to make sure it started back up with no errors and was pleased to find it booted right up perfectly.

still not sure what i need to do to be able to download that VLC though.  maybe when i get home today and try to search for it again it will work?

any ideas, suggestions, comments?

---

### Post by Facetious Falcon on 2009-02-11
Easiest way is to click applications->add/remove. Type VLC in the search bar, tick the box, apply changes and you're done.

---

### Post by jabbadahutt762 on 2009-02-11
is there a way to remotely manage via the web or something i dont have to install on my office computer?  i dont have admin rights here and all we have are wyse dummy terminals connected through a citrix system.  at home i can use putty through my LAN but i dont have the ability to get that from work.

---

### Post by Temposs on 2009-02-11
Do you have ssh capability at work?  If you do, you can set up your box at home to act as an ssh server and then you can ssh into your machine from anywhere.

Ubuntu also supports remote desktop viewing through VNC, which is installed by default. You have to give permission for your computer to be accessed that way remotely and then figure out how to access it that way from work, though.

Those are the two ways I know off the top of my head.

---

### Post by jabbadahutt762 on 2009-02-11
only way is if it were on a website and no software on this end needed to be installed.  i guess ill have to tinker with that a bit.  just thinking it would be nice to try some of these suggestions while im still at work rather than waiting until i get home.

i guess i really dont need that player software to work anyway, whenever im all done configuring i will disconnect the monitor and keyboard and stick it in my server closet.

---

### Post by Temposs on 2009-02-11
VLC is actually one of the better media players on Linux. I basically go to it when something won't play anywhere else. It's really easy to install it. 

In general, you don't need to go to a software vendor's website in order to find installation directions. Just use the Add/Remove GUI and you'll have VLC up and running in no time.

---

### Post by avtolle on 2009-02-11
Be sure all the repos (other than proposed and backports) are enabled to install VLC through Add/Remove or Synaptic. Check on Software Sources or through Synaptic to see what repositories are enabled. Check all but the backports and proposed, and reload, then look for VLC again.

---

### Post by jabbadahutt762 on 2009-02-11
> **Temposs said:**
> VLC is actually one of the better media players on Linux. I basically go to it when something won't play anywhere else. It's really easy to install it. 

In general, you don't need to go to a software vendor's website in order to find installation directions. Just use the Add/Remove GUI and you'll have VLC up and running in no time.

ok, i tried a different route i guess and when i searched for VLC nothing was coming up.  i love the vlc and use it exclusively over everything else.  why bother using multiple media players when vlc handles everything?

anyone here use linux as a media box?  im curious how it handles blue-ray media.

---

### Post by Temposs on 2009-02-11
As for media players, I love rhythmbox(Ubuntu's default music player) for playing music, and would choose it any day over vlc for that purpose. rhythmbox's UI is much more polished for handling music collections, easy to use, it mirrors the itunes interface, and it comes with lots of sweet plugins like DAAP music share, Last.fm, Jamendo, and Magnatune. You can really have a nice music listening experience with Rhythmbox, in my opinion.

Ubuntu's default movie player(totem), on the other hand...well, it's just not where it needs to be yet. For that reason I usually watch movies and such with vlc.

---

### Post by jabbadahutt762 on 2009-02-11
> **Temposs said:**
> As for media players, I love rhythmbox(Ubuntu's default music player) for playing music, and would choose it any day over vlc for that purpose. rhythmbox's UI is much more polished for handling music collections, easy to use, it mirrors the itunes interface, and it comes with lots of sweet plugins like DAAP music share, Last.fm, Jamendo, and Magnatune. You can really have a nice music listening experience with Rhythmbox, in my opinion.

Ubuntu's default movie player(totem), on the other hand...well, it's just not where it needs to be yet. For that reason I usually watch movies and such with vlc.

hmm  good to know, havent tried to run any of my music through it yet.  ill check that out when i get home if i can find a spare set of speakers.

---

### Post by jabbadahutt762 on 2009-02-12
> **jabbadahutt762 said:**
> hmm  good to know, havent tried to run any of my music through it yet.  ill check that out when i get home if i can find a spare set of speakers.

worked like a charm!  also was able to get the VLC installed finally, just had to play with that app a bit and figure it out.  

also got apache 2.0 and the ftp server up and running last night.  all i need to do now is figure out how to configure the apache.  it seems like ver 1.3 was much easier to use and configure.  also i used the windows version so maybe thats part of the difference but the config file was all in one file previously and i guess in 2.0 they decided to break it up into several config files.

anyone familiar with configuring the FTP server?  i used to use ServUFtp on windows.  not sure how to set up user folders and stuff like that.

i guess i just need to know where to look to find the configuration files for the ftp.  it didnt create any kind of access through gnome, im guessing its strictly prompt based?

---

### Post by Temposs on 2009-02-12
I would recommend to set up the computer as an ssh server rather than ftp. It is more secure, as all transactions are encrypted.

It's actually very easy to do that. All you need to do is start up the ssh daemon. You just need to run:

```
/usr/sbin/sshd
```

Then you will be able to use all the various ssh methods. There's straight ssh. If you just want to transfer files, then you can use scp. If you want to mount a remote directly via ssh so that it looks like a local folder, you can use sshfs.

Very easy, more flexible and more secure than ftp.

---

### Post by jabbadahutt762 on 2009-02-12
OK, i thought that i had downloaded the FTP server with SSH support.  im not all that familiar with SSH at all though.  i guess ill have to do more research on that.  for right now, i just need to be able to FTP in to upload web pages from Dreamweaver.  at first it will be 100% through the LAN.  isnt there a way to limit the incoming connections to just local ip's?  ill only need 1 login and 1 path then i think.

---

### Post by RVA Dennis on 2009-02-12
> **Temposs said:**
> There are lots of folks posting to this forum in a lot worse shape than you in terms of computer knowledge.

I think marking this forum section 'Absolute Beginner Talk', flaming is kept to a minimum, and an atmosphere of safety and helpfulness is generally fostered pretty well here, I think.

Good luck!

That is an absolute as flaming neophytes seems to be de rigeur on many, many forums I have used/joined.

A terrific help to me thus far into my return to Linux.

---

### Post by jabbadahutt762 on 2009-02-12
yeah for sure!  im really liking the support ive been getting thus far.  im seriously thinking ill be switching exclusively to linux soon.  my good friend is a linux guru and hes a dick.  hence why im not even bothering to talk to him about this, even though i know he can help me with all this stuff.

---

### Post by BigBananaMan on 2009-02-12
If you want to limit incoming access to specific IP addresses or domains, you can edit two config files /etc/hosts.allow and /etc/hosts.deny.  You can find more information at this page [http://www.itc.virginia.edu/unixsys/sec/hosts.html]("http://www.itc.virginia.edu/unixsys/sec/hosts.html")

One of the biggest things I noticed about Linux is the geek community that is ready, willing, and fully enabled to help any newcomer like you and I unlike Windows where everybody just copy/pastes the same answers from the Microsoft web site(is it plugged in?  Is your monitor on?  Have you tried installing the drivers again?  Is your sound muted?).  I suggest you do like I am and stop by the library sometime to pick up some "for dummies" books or anything applicable to what you want to do, it's good to learn the why to as well as the how to.  I only wish I had started using Linux 7 years ago in high school when I first learned about it.  Tell your guru buddy that if he really was competent with Linux, he would be capable of helping people and not hoarding his knowledge to himself :P

---

### Post by jabbadahutt762 on 2009-02-12
i hear ya   i got the ubuntu book free pdf and printed it up and have been browsing through as i came to things that confused me.  dummy books are a good idea but i dont have spare cash to spend.  if only borders had a copy machine ;) thats why i built the box out of spare parts and installed a free OS.  that and i wanted a server that was more secure than running apache through windows. the most irritating thing i think is the complete night and day difference in the file system from windows.  i, like you, wish i had taken this more seriously 10+ years ago when i was in high school.  i know a good deal about DOS and thats really no help with linux.  its taking me forever to navigate through the file system.  im sure ill come to terms with it soon enough but i admit its very cumbersome at first glance.

---

