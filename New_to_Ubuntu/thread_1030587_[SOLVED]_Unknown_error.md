---
title: "[SOLVED] Unknown error"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by augie2051 on 2009-01-04
I was trying to instal the video converter identified in the how to guide and received the following error.  Dont know what i did wrong or better yet how to correct???
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by halitech on 2009-01-04
which video converter were you trying to install?

also, open a terminal and do
```
sudo apt-get update
```then
```
sudo apt-get install -f
```
this will fix any broken packages

---

### Post by augie2051 on 2009-01-04
winrff i believe.  I tired what you said and this is the output:
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by augie2051 on 2009-01-04
This is what i was doing:
Copy and paste the following command into the terminal to add the new WinFF repository:

echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

This second command will merely install something called a GPG Key, so will not need editing by anyone:

wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update

Finally, execute the command below to install the applications needed for video conversion and editing:

sudo apt-get install avidemux ffmpeg winff

---

### Post by halitech on 2009-01-04
you could try adding it manually in your sources.list file
```
gksu gedit /etc/apt/sources.list
```
then save the file
then run ```
wget http://winff.org/ubuntu/AAFE086A.gpg
``` 
```
sudo apt-key add -&& sudo apt-get update
```

also make sure you don't have Synaptic running at the same time

---

### Post by augie2051 on 2009-01-04
I'm going to try and installing the way you said.  however i just ran this as sudo and fixed my earlier problem do you know what it means and what i did?  dpkg --configure -a

---

### Post by augie2051 on 2009-01-04
I think ive found the problem when downloading "Configuring sun-java6-bin" my computer battery ran out and turned off.  When i restarted it was trying to find the file.  No i have this screen and i cant seem to go forward from here to finish the download.  it looks much like a user agreement from a windows program.  there is an ok spot at the bottom but i cant seem to click on it or advance from there to finish the download

---

### Post by oldos2er on 2009-01-04
Use the Tab key to highlight "ok" ( in the Java EULA), then press Enter.

---

### Post by augie2051 on 2009-01-04
Problem solved thanks

---

