---
title: "Privoxy"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by sanjeevpunj on 2008-12-21
I managed somehow to find a privoxy package, but when I did install it eventually,it installed itself somewhere else, instead of the ETC folder.I tried to move this installed privoxy folder into the ETC folder but could not do that because of "permission denied" and I am not logged in as root.

Now what should I do? Delete the installation, and try again with some different commandline to install in the proper folder? 

I used tar -xzvf [file location/filename] to install this package 

I am not too well versed with the syntax yet, maybe I specified the location of the file itself as the path where it should be installed!

help...

---

### Post by oldos2er on 2008-12-21
You can download a *deb file here: [http://sourceforge.net/project/showfiles.php?group_id=11118&package_id=35042&release_id=627607](http://sourceforge.net/project/showfiles.php?group_id=11118&package_id=35042&release_id=627607)

 that will insure the program's installed correctly.

---

### Post by snova on 2008-12-21
Privoxy is in the repos. You needn't install this way.

---

### Post by Bunce The Dunce on 2008-12-23
Hello there!

I am a real noob when it comes to Linux/Ubuntu.

So far, I like it, it's really stable, but I'd like to be very secure and run tor/privoxy and I am having a lot of trouble, even after reading the tutorials.

I d/l'ed the files with Synaptic - I installed tor buttun for FFox, but when I run tor check, I get the message I am not running tor and it brings up my regular IP addy.

It seems like I have tried everything, and I apologize for my ignorance, but can anyone help me with this?

:confused:

Privoxy seems to be up, it is blocking ads - but tor check still fails.

I installed torx and it can't even find tor...

---

### Post by SamNSane on 2008-12-23
One thing that can make life difficult in Linux is if you try too many different approaches all at once when trying to get something to work. I'm going to suggest that you use Synaptic (and any other means necessary) to remove all directly related software (Tor, Privoxy, Torx, Torbutton etc.) from your system so that you can start over with a clean slate.

The directions I'm providing you here have worked for me on every Hardy and Intrepid system (6 in all) that I've configured. I hope that I haven't left out anything. I actually write up procedures as I configure systems so that it goes more smoothly next time around. I try to refine these procedures with subsequent installations, so I think this procedure will probably work for you if you follow it carefully.

Here we go.

First: Install Privoxy from the Ubuntu repositories.

Second: Do not use the Tor packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes. You need to add software sources that hold later, safer versions of Tor to your software sources list.

Break the Tor installation process down into a) Adding Software Sources, b) Adding a Verification Key to Your Keyring, and c) Installing the Software.

a) Adding Software Sources:

Open Synaptic, going into the Settings menu, and choosing Repositories. On the Third Party tab of the Software Sources dialog you click the +Add button then add the lines below to the list. For tor's stable version (for amd64 and i386), add these repositories to your Software Sources:

  deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) <DISTRIBUTION> main
  deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) <DISTRIBUTION> main

where <DISTRIBUTION> should be replaced with either dapper, feisty, gutsy, hardy or intrepid, depending upon which version of Ubuntu you are running.

b) Adding a Verification Key to Your Keyring:

Verifying signatures with apt 0.6.x

You should add weasel's key to your apt-keyring, so it can verify the software sources when you go to install Tor:

  $ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
  $ gpg --fingerprint 94C09C7F

should show you:

   pub   1024D/94C09C7F 1999-11-10
         Key fingerprint = 5B00 C96D 5D54 AEE1 206B  AF84 DE7A AF6E 94C0 9C7F
   uid       [ultimate] Peter Palfrader
   [...]

When that process is done issue this command:

  $ gpg --export 94C09C7F | sudo apt-key add -

to add the key to apt's keyring. 

c) Installing the Software:

To install Tor packages, issue the following commands in a terminal window:

  $ apt-get update
  $ apt-get install tor

- Final Touches -

Now that Privoxy and Tor have been installed, go to [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en) and follow the Step Two instruction for altering the Privoxy configuration file.

Finally, add Torbutton to Firefox through the browser's add-ons feature so that you can toggle Tor on / off as by clicking on the onion icon in the browser's status bar.

- End of Procedure -

On every system I've configured using this process, the Torcheck has worked first time and every time. I hope it works for you.

---

### Post by sanjeevpunj on 2008-12-23
Thanks for all those replies. Though I cannot personally thank all of you,I can say I have eventually started TOR and PRIVOXY, bothrunning fine, but now I cannot even use either in a practical sense, because when I configured the connection settings, I was foxed by the way the FOXYPROXY add-on plays around with switching TOR. It surely looks interesting to be able to switch TOR/OFF using the TOR Button, and FOXY PROXY seems to be helpful in choosing whether to use TOR, or NOT to use TOR. However the setting did not work. here they are :-

Http proxy: localhost, 8118
same for others except Socks
Socks Proxy:localhost,9050
SOCKS proxy SOCKSV5

Maybe something is wrong with these settings, I am not sure what.

---

