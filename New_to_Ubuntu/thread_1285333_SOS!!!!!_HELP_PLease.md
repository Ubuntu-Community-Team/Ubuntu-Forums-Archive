---
title: "SOS!!!!! HELP PLease"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by kutas26 on 2009-10-07
Dear Users,

I am completely new to kubuntu and linux distributions. I have no idea whatsoever of programming codes or how to use this. Ive gone through some tutorials for ubuntu linux interface but apparently it wasnt the version i am using. I am a window's user and i am not entirely acquainted with its use as well.I grew so fed of windows that i, upon being told by a friend, had someone download and install kubuntu. I believe ive screwed with everything or at least i think i do. I cant hear the sound anymore, the software manager gives me an error that the list has to be rebuilt or something. Here is the last of what i did. I dont know where to start fixing all of this but can someone please guide me? the last putative blunder that i think i made was this: i went to this site [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) and tried to follow the instructions this is what my terminal looked like after i did follow them: 
sunny@ubuntu:~$ sundo apt-get install alsa-base alsa utils
bash: sundo: command not found                            
sunny@ubuntu:~$ sudo apt-get #alsaconf
[sudo] password for sunny:            
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
Usage: apt-get [options] command                             
       apt-get [options] install|remove pkg1 [pkg2 ...]      
       apt-get [options] source pkg1 [pkg2 ...]              

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.                                                     

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade           
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages                                   
   autoremove - Remove automatically all unused packages      
   purge - Remove packages and config files                   
   source - Download source archives                          
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)         
   dselect-upgrade - Follow dselect selections                 
   clean - Erase downloaded archive files                      
   autoclean - Erase old downloaded archive files              
   check - Verify that there are no broken dependencies        

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors            
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation              
  -y  Assume Yes to all queries and do not prompt      
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable              
  -u  Show a list of upgraded packages as well                     
  -b  Build the source package after fetching it                   
  -V  Show verbose version numbers                                 
  -c=? Read this configuration file                                
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual         
pages for more information and options.                            
                       This APT has Super Cow Powers.              
sunny@ubuntu:~$ #compizconfig
sunny@ubuntu:~$ sundo apt-get install alsa-base alsa utils
bash: sundo: command not found                            
sunny@ubuntu:~$ sudo apt-get #alsaconf
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
Usage: apt-get [options] command                             
       apt-get [options] install|remove pkg1 [pkg2 ...]      
       apt-get [options] source pkg1 [pkg2 ...]              

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.                                                     

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade           
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages                                   
   autoremove - Remove automatically all unused packages      
   purge - Remove packages and config files                   
   source - Download source archives                          
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)         
   dselect-upgrade - Follow dselect selections                 
   clean - Erase downloaded archive files                      
   autoclean - Erase old downloaded archive files              
   check - Verify that there are no broken dependencies        

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors            
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation              
  -y  Assume Yes to all queries and do not prompt      
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable              
  -u  Show a list of upgraded packages as well                     
  -b  Build the source package after fetching it                   
  -V  Show verbose version numbers                                 
  -c=? Read this configuration file                                
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual         
pages for more information and options.                            
                       This APT has Super Cow Powers.              
sunny@ubuntu:~$ sudo apt-get -y remove compiz-core desktop-effects
Reading package lists... Done                                     
Building dependency tree                                          
Reading state information... Done                                 
E: Couldn't find package desktop-effects                          
sunny@ubuntu:~$ wget [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
--2009-10-08 02:09:57--  [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18                         
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.      
HTTP request sent, awaiting response... 404 Not Found                     
2009-10-08 02:09:58 ERROR 404: Not Found.                                 

sunny@ubuntu:~$ wget [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg) sudo apt-key add dd800cd9.gpg
--2009-10-08 02:10:44--  [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18                         
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.      
HTTP request sent, awaiting response... 404 Not Found                     
2009-10-08 02:10:45 ERROR 404: Not Found.                                 

--2009-10-08 02:10:45--  [http://sudo/](http://sudo/)
Resolving sudo... failed: Name or service not known.
wget: unable to resolve host address `sudo'         
--2009-10-08 02:10:45--  [http://apt-key/](http://apt-key/)            
Resolving apt-key... failed: Name or service not known.
wget: unable to resolve host address `apt-key'         
--2009-10-08 02:10:45--  [http://add/](http://add/)                   
Resolving add... failed: Name or service not known.    
wget: unable to resolve host address `add'             
--2009-10-08 02:10:46--  [http://dd800cd9.gpg/](http://dd800cd9.gpg/)          
Resolving dd800cd9.gpg... failed: Name or service not known.
wget: unable to resolve host address `dd800cd9.gpg'         
sunny@ubuntu:~$ wget [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
--2009-10-08 02:11:35--  [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18                         
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.      
HTTP request sent, awaiting response... 404 Not Found                     
2009-10-08 02:11:36 ERROR 404: Not Found.                                 

sunny@ubuntu:~$  sudo apt-key add dd800cd9.gpg
gpg: can't open `dd800cd9.gpg': No such file or directory
sunny@ubuntu:~$ wget [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
--2009-10-08 02:12:14--  [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18                         
Connecting to download.tuxfamily.org|88.191.250.18|:80... ^[[Aconnected.  
HTTP request sent, awaiting response... 404 Not Found
2009-10-08 02:12:15 ERROR 404: Not Found.

sunny@ubuntu:~$ wget [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg) sudo apt-key add dd800cd9.gpg
--2009-10-08 02:12:21--  [http://download.tuxfamily.org/3vldeb/dd800cd9.gpg](http://download.tuxfamily.org/3vldeb/dd800cd9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-10-08 02:12:21 ERROR 404: Not Found.

--2009-10-08 02:12:21--  [http://sudo/](http://sudo/)
Resolving sudo... failed: Name or service not known.
wget: unable to resolve host address `sudo'
--2009-10-08 02:12:22--  [http://apt-key/](http://apt-key/)
Resolving apt-key... failed: Name or service not known.
wget: unable to resolve host address `apt-key'
--2009-10-08 02:12:22--  [http://add/](http://add/)
Resolving add... failed: Name or service not known.
wget: unable to resolve host address `add'
--2009-10-08 02:12:22--  [http://dd800cd9.gpg/](http://dd800cd9.gpg/)
Resolving dd800cd9.gpg... failed: Name or service not known.
wget: unable to resolve host address `dd800cd9.gpg'
sunny@ubuntu:~$ sudo apt-get update
E: Type 'wget' is not known on line 55 in source list /etc/apt/sources.list
sunny@ubuntu:~$ sudo apt-get -y upgrade
E: Type 'wget' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
sunny@ubuntu:~$ sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extralibcompizongconfig-backend-gconfig
E: Type 'wget' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
sunny@ubuntu:~$ sudo apt-get -y remove compiz-core desktop-effects
E: Type 'wget' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I cant make heads nor tails of this. I sound like a hopeless case. Id apprecaite it if someone could guide me. 

Regards 
kutas

---

### Post by orngjce223 on 2009-10-07
Compiz is already included in Ubuntu.  Right-click on your desktop, select the "Effects" tab, then select the "Extra!" (or whatever it was) radio button.  It'll check to see if you have good graphics cards that can handle it, and if you do, it'll turn all the cool stuff on :D

---

### Post by LowSky on 2009-10-07
ok first things first, CALM DOWN

Second please type your data a little bit neater, the way you have it is very messy and hard to read, use the CODE tags for anything you copy form the terminal like so

```
sudo apt-get install alsa-base alsa utils
```

Your problem was that you typed the wrong command, twice.

Then you tried this command and I have no idea why becaus eit removes Compiz but it too failed because the package, desktop-effects, doesn't exist
```
sudo apt-get -y remove compiz-core desktop-effects 
```

then you tried this
```
wget http://download.tuxfamily.org/3vldeb/dd800cd9.gpg
```

which also doesn't exist, and I have no idea what you did that for. Please pay attention to the errors that appear, it seems you tried to steamroll through doing something, what it was, I have no idea.

Your sound could be a few things, maybe we could help if you told us your computers model number or the chipset you are using.

thanks

---

### Post by alphaniner on 2009-10-07
One problem I recognize is that you seem to have added some bad lines to your sources.list.

Please post the output of

```
cat /etc/apt/sources.list
```

Although, if what you posted is only a fraction of what you've done, you might be better off reinstalling.  And reading [this]("http://tldp.org/LDP/intro-linux/html/index.html").

---

### Post by snowpine on 2009-10-07
Hi Kutas, so many problems here I don't even know where to begin... :(

First of all, you are following a random internet tutorial published in 2007 on a non-official-Ubuntu website. 

Don't follow any guide, forum posting, or random advice unless you know exactly what it does and whether or not it is specific to your version of Kubuntu!

Frankly I would suggest simply reinstalling Kubuntu (since you said you just installed it) and this time be very, very careful with any terminal commands, especially containing "sudo". (Cut & paste are your friend, this will help avoid the typos I see in your post.)

The best place to start learning more about Kubuntu is through the OFFICIAL help pages and wiki. These are kept up to date and are fairly reliable. (Information elsewhere on the web can quickly become out of date or unreliable.)

---

### Post by LowSky on 2009-10-07
> **snowpine said:**
> Frankly I would suggest simply reinstalling Kubuntu (since you said you just installed it) and this time be very, very careful with any terminal commands, especially containing "sudo". (Cut & paste are your friend, this will help avoid the typos I see in your post.)

This is probably the best advice

---

### Post by kutas26 on 2009-10-08
hey guys,

thank you so much for your responses. Its very reassuring to know that people here try their best to help you out. Having said that, i think uninstalling and reinstalling would be a pertinent thing to do, however, i am not very computer literate in these matters and would require some step by step procedure or something. Ill try my best to provide you with the details of my system. I dont know how to acquire or install windows so i normally take it to my friend. He installs the windows from a the programs that he downloads off the internet and i had him permanently install kubuntu in my system along with windows 7 the last time i approached him for this. the isntallation icon for ubuntu appears as a separate cd drive in my windows mycomputer folder.  I wish to be independent of my friend and do this myself. 
I donot have the windows installation cd. Its a dual boot  system with windows 7 installed first and then kubuntu on it. How do i, without ruining windows settings, uninstall and reinstall kubuntu in my system. I would appreciate a step by step guide for dummys if that is possible. As in even opening and clicking a particular system, terminal, folder etc etc or running the bios for me requires some elaborate explanation. I hope this isnt much of a hassle for you guys. I promise to be more careful with the kubuntu once i have it up and running again with all the default settings. 

best regards
Kutas

---

### Post by snowpine on 2009-10-08
> **kutas26 said:**
> hey guys,

thank you so much for your responses. Its very reassuring to know that people here try their best to help you out. Having said that, i think uninstalling and reinstalling would be a pertinent thing to do, however, i am not very computer literate in these matters and would require some step by step procedure or something. Ill try my best to provide you with the details of my system. I dont know how to acquire or install windows so i normally take it to my friend. He installs the windows from a the programs that he downloads off the internet and i had him permanently install kubuntu in my system along with windows 7 the last time i approached him for this. the isntallation icon for ubuntu appears as a separate cd drive in my windows mycomputer folder.  I wish to be independent of my friend and do this myself. 
I donot have the windows installation cd. Its a dual boot  system with windows 7 installed first and then kubuntu on it. How do i, without ruining windows settings, uninstall and reinstall kubuntu in my system. I would appreciate a step by step guide for dummys if that is possible. As in even opening and clicking a particular system, terminal, folder etc etc or running the bios for me requires some elaborate explanation. I hope this isnt much of a hassle for you guys. I promise to be more careful with the kubuntu once i have it up and running again with all the default settings. 

best regards
Kutas

Hmm, if that is the case, it *might* be easier and safer to rescue your current system instead. :)

Let's start with fixing your sources.list so you can install software. Please follow Alphaniner's suggestion in post #4.

---

