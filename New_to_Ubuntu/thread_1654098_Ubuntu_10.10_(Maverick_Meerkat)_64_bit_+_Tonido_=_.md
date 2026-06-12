---
title: "Ubuntu 10.10 (Maverick Meerkat) 64 bit + Tonido = Confusion!"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by MjK3II on 2010-12-27
**H**[B]ello guys! I am trying to use Tonido on my machine to stream to my iphone 4 but I am having some problems.

I saw that there was a 64 bit guide on the page and clicked that. I attempted following the instructions [/B]
(
[COLOR=Black][FONT=Tahoma]1.[/FONT][/COLOR]      Download TonidoSetup_i686.deb
 [COLOR=Black][FONT=Tahoma]2.[/FONT][/COLOR]      Double-Click on it and click "Install Package"
 [COLOR=Black][FONT=Tahoma]3.[/FONT][/COLOR]      Start Tonido from Applications->Internet->Tonido)
I keep getting stuck on the second instruction when I double click it takes me to the Ubuntu Software Center (as expected). But when I go to download the software the button to download is grayed out and unclickable. It gives me the error message "Wrong architecture 'i386'" and will not allow me to download the package,

**Since i was not able to install that the instructions say this:**
 "We don't have a Tonido package for 64 bit yet. Meanwhile, you might want to try this:  
 sudo apt-get install ia32-libs
  
 After installation, you can either launch by running tonido.sh or using GTK icon tray. 
  
 To run Tonido.sh:
  
 cd /usr/local/tonido
 ./tonido.sh start
  
 If you are trying to launch Tonido with GTK tray icon support and don't have GTK IA32, then run:
  
 sudo apt-get install ia32-libs-gtk"


**I**[B] also did that and installed both packages. I still have been unable to install Tonido. Please HELP!!
[/B]


P.S. The instructions were copied off the Tonido website and are not in bold like my typing XD.

---

### Post by MjK3II on 2011-01-01
Bump still stuck

---

### Post by hunter99507 on 2011-01-01
Do you have an intel processor or a AMD?

Also have u tried to install the 32bit version?

---

### Post by MjK3II on 2011-01-01
AMD. and yes when I downloaded the file and when I double click it it takes me to the software center but I am unable to Download because it says wrong i386 in the description area and has a greyed out download button.

---

### Post by gandaran on 2011-01-01
> **MjK3II said:**
> AMD. and yes when I downloaded the file and when I double click it it takes me to the software center but I am unable to Download because it says wrong i386 in the description area and has a greyed out download button.
you mean you cant install it with software center? if you already have downloaded the package you just need to install it, do you have installed the necessary 32-bits libs to run and install 32-bits packages on 64-bits systems first?
for installing try using 'gdebi' (install 'gdebi' from package manager) or you can try force installing the package from the command line.

---

### Post by MjK3II on 2011-01-01
I just tried to post a picture of the screen shot of my problem but it just gave me the location of the picture. How would I post a screen shot on this forum? 

I installed 'gdebi' but I am unsure what to do with it... and what is the command for force installing a package..? Im sorry but I've only copy and pasted into the command line. Im not sure of what any of the commands are besides 'apt-get install ...'

---

### Post by spade on 2011-01-02
Yeah, Tonido is confusing with providing a called "i686" package, although it is a i386 one. I have an Intel and I get the same error message.
You can sort this out with the following command:
```
sudo dpkg --force-architecture -i /PathTo/TonidoSetup_i686.deb
```
The problem is that once the package is installed, nothing happens when clicking on the icon. Same thing with the command line linked to the icon:
```
/usr/local/tonido/tonidostart.sh
```
A process is remaining in memory when launching:
```
/usr/local/tonido/tonido.sh start
```
But nothing appears, even with reclicking on the icon.

---

### Post by MjK3II on 2011-01-02
I copy and pasted the code you pasted and then i got the error: 

dpkg: error processing /PathTo/TonidoSetup_i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /PathTo/TonidoSetup_i686.deb

Therefore I was not able to install the program. Why would I receive the above error (if you know)?
The second and third part of the post confuse me because I am unable to get that far. Are you saying that even though Tonido was able to be installed it will not open through the graphic icon nor the command? 
The third section is completely lost on me.

I'm sorry Ive been using Ubuntu for a very short time and have had no command experience before and I believe therein lies my confusion.

P.S. How did you put the box around the command?

---

### Post by spade on 2011-01-03
Lol... sorry, I was not clear enough for you. You should replace "/PathTo/TonidoSetup_i686.deb" with the actual full path (path + file name) of the file "TonidoSetup_i686.deb", at the location where you downloaded it to. For me, it is "/Home/sspade/Download/TonidoSetup_i686.deb", but it is probably different for you.
I am stuck afterward, so I am curious about how it works for you.

PS: click on "#" at the top toolbar as editing your post, and you can carry on writing between start and end code tags. Before submitting, you can preview.

---

### Post by MjK3II on 2011-01-03
I couldnt get the application to open like a window as expected either. But when I entered the command 

```
cd /usr/local/tonido
 ./tonido.sh start
```My Terminal "name"  was this: 
```
michael@michael-ubuntu:/usr/local/tonido$
```Instead of this:

```
michael@michael-ubuntu:~$
```Im not sure what this means though. I will experiment further.

also after entering that command there was a process called "tonidoconsole" running but it was "sleeping"

P.S. What is the term used that I described by "name"

P.S. x2 I joined the Tonido support forum in hopes of getting help from an admin and will keep you posted!

---

### Post by spade on 2011-01-04
I think the terminal "name" is actually the "invite".
At the moment I find SpiderOak is the best solution for online backup, with a very light foot print command line version. It is multi-platform and works out of the box.

---

### Post by MjK3II on 2011-01-04
After using the command I used to start tonido i tried opening my browser and opening [http://127.0.0.1:10001]("http://127.0.0.1:10001/") to check if it is working.
  					
This produced actual results and I was able to get the application to work!

---

### Post by spade on 2011-01-04
Thanks fo the tip ! The web interface is very nice. But then I realised that Tonido is a sharing system without any available storage area. I understood that "Tonido Cloud" will provide this service when it is released, but there will be no free and limited account type.
There is also a local backup feature, but it is very basic so I'll keep BackInTime for this function.
Thanks anyway !

---

