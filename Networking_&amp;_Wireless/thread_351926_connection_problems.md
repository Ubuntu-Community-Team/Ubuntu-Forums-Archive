---
title: "connection problems"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by sh0rtbus56 on 2007-02-02
i can't seem to connect to the internet
i have a dsl modem which works fine in windows xp
i set up teh connection in ubuntu as the help says

but still no internet connection!

---

### Post by Metaljaz on 2007-02-02
You haven't told us much about your setup. You have a DSL modem but do you connect hard wire or are you using a usb device to connect or a wireless device.
 
Try this:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

---

### Post by sh0rtbus56 on 2007-02-02
i wasn't sure what all you would need to know to help me out, sorry
i used that guide, but still no connection :(

i connect via ethernet (PPPOE)

---

### Post by Metaljaz on 2007-02-03
try this thread:

[http://www.ubuntuforums.org/showthread.php?t=183062&highlight=ppoe](http://www.ubuntuforums.org/showthread.php?t=183062&highlight=ppoe)

---

### Post by sh0rtbus56 on 2007-02-03
i really am a linux noob. how do i "install build-essential" ?
the "wget" command gave an error - "temporary failure in name resolution" but i think that is becasue i do not have build-essential installed.
the "sudo ./go" have a "command not found" error.

once these things are fixed i feel sure my itnernet will work

thanks for helping me so far! :)

---

### Post by IcarusR on 2007-02-03
In the linked thread the lines headed code which are shaded grey, like this ....
```
sudo apt-get install build-essential
```
are commands that you need to copy & paste into a terminal.
The above code will download & install build-essential which is the package needed to compile software from source.
> "wget" command gave an error - "temporary failure in name resolution"
is nothing to do with not having installed build essential. It means that the url could not be found on a DNS server.

---

### Post by sh0rtbus56 on 2007-02-03
i ran the "sudo apt-get install build-essential" but it gave me a "couldn't find package build-essential" error

confused >.>

---

### Post by IcarusR on 2007-02-03
You probably need to add repositories. Check out this guide for Edgy in general
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
& specificaly for adding repositories
[http://http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by sh0rtbus56 on 2007-02-03
in the repository help guide, to enable extra repositories, #2 says "in the installation media tab, click add"
there is no "installation media" tab
is that the right help for ubuntu 6.10?
still confused >.>

---

### Post by IcarusR on 2007-02-03
follow the instruction to do it using a terminal....
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://**gb**.archive.ubuntu.com/ubuntu](http://**gb**.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse 

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

Save the edited file

Then run the following to install the gpg key for mediabuntu

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```

Then this command to update apt-get

```
sudo apt-get update
```

Then go to Synaptic & search for the package you want to install.

---

### Post by sh0rtbus56 on 2007-02-03
i completed all those steps then tried
"sudo apt-get update"
which gave an error
"gpg: no valid OpenPGP data found." and
"temporary failure resolving archive.ubuntu.com
temporary failure resolving etc."

---

### Post by DEAthKA on 2007-02-04
This a logical problem. How can I make a connection to a web site with wget when my internet connection in ubuntu is not working The PPOE tutorial is in this case wrong.

---

### Post by sh0rtbus56 on 2007-02-04
@ deathka 
wget DOES in fact work as long as your computer has a good connection to the internet, even though linux doesn't recognize the connection
it doesn't make sense to me either

---

