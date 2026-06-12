---
title: "VLC displays no video or audio- flies thru timeline. PLease help!"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by hatcherdogg on 2009-03-30
Hello-

First off, I am as new as it gets. I am very comfortable in Win environment, but Ubuntu is brand new to me. I am excited to learn!

Ok- running Hardy Heron 8.04 on a Dell Mini 9, VLC installed. 

I am trying to play video files- mp4, vlc, avi, etc, all of which I can view the same files on windows thru vlc.

I have no clue what to do. Tried to install something from a post I read about repositories- but still not working. 

Thanks in advance for your help and knowledge.

---

### Post by metallicamaster3 on 2009-03-30
[COLOR=black]Open up a terminal and copy/paste this: be prepared to enter your password.

"sudo gedit /etc/apt/sources.list"

From there, look for lines beginning with "# deb ..." there should be around 4 of them. Take out the # in them, making them look like the others (like "deb ..."). Save the file, then close out.

In the terminal again, type "sudo apt-get update" then "sudo apt-get upgrade"

After the upgrade, do "sudo apt-get install [COLOR=#3333FF]ubuntu-restricted-extras" 

After that you should be set! For more info; [http://www.ubuntumini.com](http://www.ubuntumini.com)
[/COLOR][/COLOR]

---

### Post by kansasnoob on 2009-03-30
First install ubuntu-restricted-extras either from Synaptic or go to terminal and run:

```
sudo apt-get install ubuntu-restricted-extras[CODE]

And, there's this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

or this:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

Personally I do this using Synaptic:

search totem and install:

totem-mozilla
totem-plugins-extra
totem-xine

then search (still in Synaptic) vlc and install:

mozilla-plugin-vlc

(all of the above will ask you to approve installation of dependencies which you must do)

Then go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Assuming this is 8.04 go to terminal and:

[CODE]sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Don't forget the gpg key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

And then:

```
sudo apt-get install libdvdcss2
```

and:

```
sudo apt-get install w32codecs
```

I'm assuming you're not running 64 bit Ubuntu!

---

### Post by tahitiwibble on 2009-03-31
And if you still have any problems, [this procedure]("http://linuxowns.wordpress.com/2008/03/18/messed-up-picture-with-vlc/") has helped me a couple of times with various vlc problems.

---

