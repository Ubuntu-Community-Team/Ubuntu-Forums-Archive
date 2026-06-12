---
title: "How to install script?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by TigerEar on 2010-04-03
Hey guys

Ive had Ubuntu for about 3 days now and I'm loving it so far - as far as I can see, there's nothing that can't be done with this that I used to do with Windows.

I run a fairly finicky laptop, it's a Dell XPS M1330. Ubuntu doesn't give me as good battery life as Windows did but I found a thread here that says it can fix that.

[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

Can anybody tell me how to install these "scripts"?

Thanks

Tiger

---

### Post by tica vun on 2010-04-03
The instructions in that thread are pretty clear, can you tell us precisely which part you didn't understand?

---

### Post by TigerEar on 2010-04-03
It's just difficult coming from a Windows-only background and understanding what that kind of thing means. I used to control my laptop's voltage and power consumption through a couple of GUI programs and I think this thread makes the assumption that people know what to do.

Do I save it as a text file and then install it with Gutsy? What is Gutsy?

Sorry for being a bit dumb at this, but I literally have no idea what he's talking about.

---

### Post by HPD2 on 2010-04-03
Gusty is Ubuntu 7.10.
[https://wiki.ubuntu.com/GutsyGibbon](https://wiki.ubuntu.com/GutsyGibbon)

for the scripts just copy and paste them in to gedit and save it as whatever.sh
Then you need to open the terminal and change directory to ware you saved the script lets say on the desktop
```
cd Desktop
```Next to make it executable do 
```
sudo chmod +x whatever.sh
```then execute it by
```
 sudo ./whatever.sh
```

---

### Post by WelshChris on 2010-04-03
There's a gnome applet for controlling cpu frequency which may be useful.

Right click on the panel, then add to panel, then click on cpu frequency monitor.

(This is on Karmic, I assume it applies to Gutsy also, I'm sure someone will correct me.)

Chris

---

### Post by TigerEar on 2010-04-03
Hey, I tried those instructions and they didn't work. Also, they're different to what the thread stated. Still don't know how to do this.

---

### Post by TigerEar on 2010-04-04
Can anybody help me? I follow the instructions in the original thread but when I enter "sudo install 99-savings /etc/pm/sleep.d" the Terminal tells me that there's no such file or directory. The file is saved as a .sh file on my Desktop directory and even if I change the Terminal directory to Desktop it still doesn't work for some reason.


Haaaaalp plz thx bi

---

### Post by abeisgreat on 2010-04-04
Open up a terminal

Applications > Accessories > Terminal
and type
```

ls /etc/pm

```
what does it say?

Edit: Wait, does it say there is no /etc/pm/sleep.d or no 99-savings? Because if there is no 99-savings, try renaming your script to that.

---

### Post by TigerEar on 2010-04-04
it says config.d  power.d  sleep.d

The script 99-savings is on my desktop

---

### Post by abeisgreat on 2010-04-04
> **TigerEar said:**
> it says config.d  power.d  sleep.d

The script 99-savings is on my desktop

Then type 
```

cd Desktop

```
then run the other command.

---

### Post by TigerEar on 2010-04-04
I tried that, and this is what I got:

```
matt@Grasshopper:~$ ls /etc/pm
config.d  power.d  sleep.d
matt@Grasshopper:~$ cd Desktop
matt@Grasshopper:~/Desktop$ sudo install 99-savings /etc/pm/sleep.d
[sudo] password for matt: 
install: cannot stat `99-savings': No such file or directory
matt@Grasshopper:~/Desktop$
```

---

### Post by abeisgreat on 2010-04-04
> **TigerEar said:**
> I tried that, and this is what I got:

```
matt@Grasshopper:~$ ls /etc/pm
config.d  power.d  sleep.d
matt@Grasshopper:~$ cd Desktop
matt@Grasshopper:~/Desktop$ sudo install 99-savings /etc/pm/sleep.d
[sudo] password for matt: 
install: cannot stat `99-savings': No such file or directory
matt@Grasshopper:~/Desktop$
```

Then the file 99-savings does not exist. You must create it, as I assume was covered in the tutorial.

---

### Post by anewguy on 2010-04-04
The opening post of that thread shows the script - highlight it, right-click and click copy, then open an editor (such as gedit) and paste into it.  It states right after the script "name it 99-savings", so in the editor do a save-as and put 99-savings in the file name.  After the file is saved, close the editor and continue on with the post.

Dave ;)

---

### Post by TigerEar on 2010-04-04
I think it's fixed - the first poster told me to save it as .sh so I did, but when I converted it to just a normal text file it worked fine.

When I entered those commands it didn't give me any error messages, I assume that means it worked? How do I make that script run on startup?

---

### Post by quinnten83 on 2010-04-04
> **TigerEar said:**
> Can anybody help me? I follow the instructions in the original thread but when I enter "sudo install 99-savings /etc/pm/sleep.d" the Terminal tells me that there's no such file or directory. The file is saved as a .sh file on my Desktop directory and even if I change the Terminal directory to Desktop it still doesn't work for some reason.


Haaaaalp plz thx bi

rightclick on the .sh file,
select properties, then select the permission tab, on that tab select, allow to execute as a program".
close the properties windows and then double click the file.
select execute or something similar and the script will run, you don't install these. they are like a batch script in windows.

---

### Post by TigerEar on 2010-04-04
Cheers guys, thanks for all of your help - this one is solved

Thanks again

---

