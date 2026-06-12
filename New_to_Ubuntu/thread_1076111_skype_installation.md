---
title: "skype installation"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by chirucam on 2009-02-21
hi, i did a search for skype in synaptic manager, but nothing came out.. how do i install skype on my ubuntu 8.04? please help..

---

### Post by konqueror7 on 2009-02-21
type in your terminal...
```
sudo gedit /etc/apt/sources.lst
```

then add this line...
```
deb http://download.skype.com/linux/repos/debian stable non-free
```

then in the terminal again...
```
sudo apt-get update
```

now you should be able to install it via synaptic or apt-get...
```
sudo apt-get install skype
```

---

### Post by chirucam on 2009-02-21
hi im too new to ubuntu.. tried what conqueror7 told me to do, but it didnt work..maybe im doing something wrong.. please could you explain exactly what to do once i go to terminal? i was doing copy paste what conqueror had written on his post, but it asks for password and when i give password, nothing happens..please help.. thanks.

---

### Post by konqueror7 on 2009-02-21
oh, okay...just select a method below...
[B]
Method 1[/B]
1) open terminal and enter the following lines...
```
sudo gedit /etc/apt/sources.lst
```
it will ask you your root password, enter it, a file containing several text will open

2) now, enter the following line to the end of the file (the one you opened earlier)
```
deb http://download.skype.com/linux/repos/debian stable non-free
```
save the file, and exit

3) again, in the terminal, enter the following lines...
```
sudo apt-get update
```
this will again prompt for your root password, enter it, it will then update your repository list

4) now in the terminal again, enter...
```
sudo apt-get install skype
```
it will again prompt for the root password, enter it, it will then download and install skype. after the installation, check in Applications > Internet menu


**Method 2**
1) you can download UbuntuTweak (application that helps you tweak your ubuntu, including installation of 3rd party apps) [here]("http://ubuntu-tweak.com/")

2) you can install skype by going, Application > Add/Remove in the UbuntuTweak app


**Method 3 (7.04-8.04)**
1) download skype directly from their [site]("http://www.skype.com/go/getskype-linux-ubuntu")

2) double click it, and will prompt for your root password, and will install skype

i usually use the first method because it helps me keep my skype updated if any new release is out...

---

### Post by nns2006 on 2009-03-29
When i tried to Install following the  1st  method i am getting this msgs:-

nityanand@nityanand-laptop:~$ sudo gedit /etc/apt/sources.lst
[sudo] password for nityanand: 
nityanand@nityanand-laptop:~$ sudo apt -get update
sudo: apt: command not found
nityanand@nityanand-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Reading package lists... Done
nityanand@nityanand-laptop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype

for second method it says that wrong architecture.I will prefer to do via 1st one
Please help

---

### Post by mikewhatever on 2009-03-29
Skype is not in the standard repositories. Just download a .deb from skype's web site.

---

### Post by nns2006 on 2009-03-29
> **mikewhatever said:**
> Skype is not in the standard repositories. Just download a .deb from skype's web site.

That is true but i want to make one for skype. Is it not possible ?

---

### Post by diablo75 on 2009-03-29
> **nns2006 said:**
> That is true but i want to make one for skype. Is it not possible ?

Make one WHAT for skype?

---

### Post by nns2006 on 2009-03-29
> **diablo75 said:**
> Make one WHAT for skype?

I want to add skype to repos. How to do that?

---

### Post by diablo75 on 2009-03-29
> **nns2006 said:**
> I want to add skype to repos. How to do that?

The first reply you got in this thread told you how.  Here's a slightly different way to go about doing it:

1.  Click System>Administration>Software Sources
2.  Click the Third Party tab at the top.
3.  Click the Add button and paste in the following text:
```
deb http://download.skype.com/linux/repos/debian stable non-free
```
4.  Click the Add Source button, and then the Close button to the main window.
5.  Click the Reload button when prompted to.

From here you can do one of the two following things:

1.  Click System>Administration>Synaptic Package Manager and search for skype, and then mark it for installation.
2.  Open a terminal window and type **sudo apt-get install skype** and press enter.

If neither of these two methods work, then you'll just have to resort to downloading the deb file from skypes website manually and double-click on it when it's finished downloading to install (which, in my opinion, is faster and easier).

---

### Post by 3rdalbum on 2009-03-29
A little bit off-topic, but why are you telling the original poster to manually edit a text file when Ubuntu has a perfectly-good Software Sources program to perform the same task? Every day there are posts from people complaining that their package manager isn't working, and it turns out that they've made a mistake manually editing their sources.list.

I'm not annoyed, I'm just a bit mystified. Plus it gives people the impression that they have to use the terminal for everything, which is not true.

---

### Post by nns2006 on 2009-03-29
I tried to install by adding the third party software but i failed. I downloaded from the skype.com but upon double clicking it displays the massage as [COLOR="Red"]Error=wrong architecture 'i386'[/COLOR]

---

### Post by gandaran on 2009-03-29
why don't you just add the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository?
then install skype using apt-get or synaptic package manager.

---

### Post by nns2006 on 2009-03-29
how to add medibuntu repos?

---

### Post by hyper_ch on 2009-03-29
> **3rdalbum said:**
> A little bit off-topic, but why are you telling the original poster to manually edit a text file when Ubuntu has a perfectly-good Software Sources program to perform the same task? Every day there are posts from people complaining that their package manager isn't working, and it turns out that they've made a mistake manually editing their sources.list.

because the cli is the only unified thing on linux. No matter what desktop you use, no matter what package manager you use, on the cli it's all the same... and often faster...

And if you've given the according code then they don't even need to type it but they can just copy'n'paste it.


Wrong architecture is there because the skype repos have no 64bit support. Use medibuntu instead. Use the instructions given or use my repo generator in my sig.

---

### Post by gandaran on 2009-03-29
> **nns2006 said:**
> how to add medibuntu repos?
click the medibuntu link in my first post

---

### Post by cotcot on 2009-03-29
> **konqueror7 said:**
> type in your terminal...
```
sudo gedit /etc/apt/sources.lst
```

then add this line...
```
deb http://download.skype.com/linux/repos/debian stable non-free
```

then in the terminal again...
```
sudo apt-get update
```

now you should be able to install it via synaptic or apt-get...
```
sudo apt-get install skype
```

Typing error :  my repos are in sources.l[COLOR="Red"]i[/COLOR]st  (list with i)

---

### Post by nns2006 on 2009-03-29
when i am adding the medibuntu I amgetting this output in terminal
nityanand@nityanand-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package medibuntu-keyring

Now what to do?

---

### Post by gandaran on 2009-03-29
did you first run this line (FOR UBUNTU 8.04)
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
and then?
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by nns2006 on 2009-03-29
> **cotcot said:**
> Typing error :  my repos are in sources.l[COLOR="Red"]i[/COLOR]st  (list with i)

this is the result 

nityanand@nityanand-laptop:~$ sudo gedit /etc/apt/sources.list
nityanand@nityanand-laptop:~$ sudo apt-get update
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 204.9.165.82 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 204.9.165.82 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


:(

---

### Post by nns2006 on 2009-03-29
> **gandaran said:**
> did you first run this line (FOR UBUNTU 8.04)

and then?

this is the result 
nityanand@nityanand-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

---

### Post by gandaran on 2009-03-29
> **nns2006 said:**
> this is the result 
nityanand@nityanand-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
maybe the medibuntu server is out for now, try another time later on

---

### Post by gandaran on 2009-03-29
are you using a proxy internet connection?
maybe this is your problem?

---

### Post by nns2006 on 2009-03-29
no.i am not using proxy connection.

---

### Post by kiridude on 2009-03-29
I have Ubuntu 8.10 and skype is in my synaptic manager.  Maybe just upgrading will sort out a few things.

Also, let's try to support open source such as Ekiga as we can never know what agreements skype is making behind closed doors...

---

### Post by qrwe on 2009-03-29
The best tip for adding the Medibuntu repostory is to enter the URL and read howto do it, the HOWTO there is very easy and helpful to follow:
[Medibuntu repostory HOWTO]("https://help.ubuntu.com/community/Medibuntu")

Good luck!

---

### Post by fballem on 2009-03-29
The documentation for Medibuntu is at the following URL:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This includes the specific instructions for adding the Medibuntu repository to your sources list. Please make sure that you use the repository for Hardy. Cut and paste the appropriate lines using a terminal.

I do know, at one point in time, that both Hardy (8.04) and Intrepid (8.10) had the 32-bit versions of Skype in the repositories and that there were no 64-bit deb installation packages.

If you copy and paste the marked paragraph below carefully, in a terminal, then you should be able to install Skype on 64-bit Hardy. Remember that CTRL+SHIFT+V is used to paste code into terminal. It is a single line of code and is very long.

I used these reliably when I was installing on to a 64-bit installation:

Marked paragraph:

sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4

end of marked paragraph

Hope this helps,

---

