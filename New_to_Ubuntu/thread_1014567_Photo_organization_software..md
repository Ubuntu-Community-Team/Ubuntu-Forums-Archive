---
title: "Photo organization software."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Jerfo on 2008-12-18
Hello, I'm currently looking for a program to organize my pictures, nothing too fancy actually but I didn't like the over-simplified F-Spot, I'm looking for something more like Picasa or the one from Adobe whose name I forgot.

So, any recommendations?

---

### Post by aheckler on 2008-12-18
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by prabhakaran1989 on 2008-12-18
Thanks for this support!!:popcorn:

---

### Post by Jerfo on 2008-12-21
Lol duh, I had no idea they had that project! Thank you very much!

---

### Post by Jerfo on 2008-12-21
Ok so could anybody provide me with *extremely* simplified instructions for installing this? I couldn't understand most of the instructions! 

I don't know what I'm doing wrong, but nothing is working, here is what I did:

I tried with the GUI (even though it said Feisty, everything matched), followed all the instructions and still, nothing appears. I tried the command line and when I have to add 

# Google software repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free  

to the /etc/apt/sources.list.d/ directory, it tells me I can't save because I don't have the rights. So basically I don't know what to do.

---

### Post by binbash on 2008-12-21
add it with sudo : 

sudo gedit /etc/apt/sources.list

---

### Post by waspbr on 2008-12-21
there's is no need to add repos, just install the .deb files, these are somewhat equivalent to the windows executable installers. 

for a 32 bit system

[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb")

for a 64 bit system

[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb")

Good luck

---

### Post by waspbr on 2008-12-21
alternatively if you really want to add the repos

go to synaptic (System>Administration>Synaptic package manager), enter your password, there go to the Settings tab and there you go the Repositories option.

before adding the sources you need to add the key, According to the instructions  you should add these lines into a terminal window (Applications>accessories>terminal)
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
apt-get update
```

but for some reason that didn't work with me, no worries there is a work around.

download the signing key here  ([https://dl-ssl.google.com/linux/linux_signing_key.pub]("https://dl-ssl.google.com/linux/linux_signing_key.pub")), just do right click and do "save link as" and save it into your desktop, be sure to set the file type from "plain text document" to "all files"(right on top of the save button).

now you have all you need, In the repositories menu go to the authentication tab, there click on the "import a key file" button, a browser should appear, bear in mind that you are in root mode, so the root desktop is not the same as your desktop, then navigate to file system > home > yourhomename>Desktop where you should find the file 
```
linux_signing_key.pub
``` 

once you do that go to the "Third Party Software" at the repositories menu, press the "add" button and paste this line:

```
deb http://dl.google.com/linux/deb/ stable non-free  
```

press okay and go back to synaptic, there you should press the reload button (provided it doesn't already ask you to reload), once the reloading is done search for picasa in the search fields select it and apply, you are done.

---

### Post by clive littlewood on 2008-12-21
Hi

Just download the .deb file from the Picassa site.

Double click on the file and it will be installed on your system.

On installation it will look for all your photo files and compile new albums for you, and of course you can store your albums on the picassa site.      :)

Regards

Clive

---

### Post by celem on 2008-12-30
I removed F-Spot because (1) I didn't like its method of storing the photos in lots of folders organized by day, month year; (2) the current version has no edit capability, even though previous versions appear to have had some edit capability.

I loaded Picassa and it works extremely well. However, I can't get it to be set as the default application for the pop-up when an SD card is inserted as a removable drive. I use 8-10 Intrepid and the System->Preferences->Removable Drives tool is missing. Any ideas?

---

