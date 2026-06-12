---
title: "How do I install this? linux-installer.bin"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by listerdl on 2009-04-21
Hi I am baffled - how do I install a .bin file?

Thanks!

---

### Post by pspsampsp on 2009-04-21
you have to go into terminal (applications -> Accessories -> Terminal ) and go to the directory the script is in (if it was in a subfolder of my home directory i would do "cd subfolder" in terminal) and run "sh ./linux-installer.bin" or possibly just "./linux-installer.bin"

---

### Post by ddrichardson on 2009-04-21
You might also need to set it as executable, sometimes this attribute is not set when downloaded```
chmod +x linux-installer.bin
```
What is it you're trying to install can I ask?

---

### Post by gandaran on 2009-04-21
cd the terminal to the directory where the bin file is, if you don't know how to do it move the file to home 'user' folder, open terminal and type
sudo ./*exact .bin file name*
sudo is needed if you have to run the file with root permission and probably you have to make the file executable before running the command, right click the file » properties » permissions » tick the allow executing file as program.
you can also use **sudo sh** instead ./

---

### Post by listerdl on 2009-04-21
> **pspsampsp said:**
> you have to go into terminal (applications -> Accessories -> Terminal ) and go to the directory the script is in (if it was in a subfolder of my home directory i would do "cd subfolder" in terminal) and run "sh ./linux-installer.bin" or possibly just "./linux-installer.bin"

Thanks...actually the .bin that I downloaded is located in my "Documents" Folder, (Places > Documents > then the .bin)

So does my terminal code have to be documents/linux-installer.bin?

THANKS!

---

### Post by ddrichardson on 2009-04-21
Don't forget the capital letter:```
~/Documents/linux-installer.bin
```

---

### Post by listerdl on 2009-04-22
> **ddrichardson said:**
> You might also need to set it as executable, sometimes this attribute is not set when downloaded```
chmod +x linux-installer.bin
```
What is it you're trying to install can I ask?

Of course you can ask - it is this [http://bitnami.org/stack/tracks](http://bitnami.org/stack/tracks) basically it is an organiser - looks really cool just cant seem to install - as yet!!

---

### Post by listerdl on 2009-04-22
> **ddrichardson said:**
> Don't forget the capital letter:```
~/Documents/linux-installer.bin
```

Thanks for the help but it didnt seem to work....This is what I entered into the terminal:

```
henry@DELL-laptop:~$ ~/Documents/bitnami-tracks-1.6-2-linux-installer.bin

```

The /bitnami-tracks-1.6-2-linux-installer.bin is the exact name of the file and the location is 100% in my Documents folder....

When I enter the above code the reply this reply comes from the terminal

```
bash: /home/henry/Documents/bitnami-tracks-1.6-2-linux-installer.bin: Permission denied
```

This is odd...cause it is definitely there....do you reckon it is because the program is not executable - since, as quoted above, "sometimes this attribute is not set when downloaded"

All comments greatly appreciated!!!!!!!!!

---

### Post by ddrichardson on 2009-04-22
It wants to be run with sudo```

sudo ~/Documents/bitnami-tracks-1.6-2-linux-installer.bin
```It'll ask for your password. sudo elevates your rights and is required to install software. Only do this with stuff you've downloaded and are happy to install.

---

### Post by listerdl on 2009-04-23
You are a genius.

That worked great.

On a slightly different subject - with linux and ubuntu - does it really matter where I allow the program to be installed - because following from the code I entered above it asks me where I would like to install....

Doesnt really matter does it?

THANKS VERY MUCH!!!!!!!!!!

---

### Post by ddrichardson on 2009-04-23
Generally in most distributions non-packaged or non-default software is installed to [/opt]("http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html").

Remember that software with its own installer isn't automatically updated, so wherever possible use Synaptic to install software.

---

### Post by listerdl on 2009-04-23
Thanks for your help. In fact I needed this program to run on another machine and I downloaded the same program at the same location but this time when I try and do the above it doesnt work and I get the following code:

```
henry@TOSHIBA-laptop:~$ ~/Documents/bitnami-tracks-1.6-2-linux-installer.bin

bash: /home/henry/Documents/bitnami-tracks-1.6-2-linux-installer.bin: Permission denied

```

Any ideas why this doesnt work - please note that the .bin folder is located in the Documents folder....

---

### Post by ddrichardson on 2009-04-23
Yes, you forgot the sudo again:```

sudo ~/Documents/bitnami-tracks-1.6-2-linux-installer.bin
```Linux allows different users different rights to run programs and access files and devices. Typically there is a single user who can do anything and not be questioned - the root user.

Ubuntu doesn't enable the root account but uses sudo to grant elevated rights when needed, provided that user is listed along with what they can do in a file called /etc/sudoers.

Here, where you want to install software, because this requires elevated rights you need to use the sudo command before the program you want to run.

---

