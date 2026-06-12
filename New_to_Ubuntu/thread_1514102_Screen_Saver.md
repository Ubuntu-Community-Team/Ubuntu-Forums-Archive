---
title: "Screen Saver"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Shenachie on 2010-06-20
I run a busy guest house and yesterday our guest computer lost wireless access. That prompted me to install Ubuntu 10.04 and lo the issue was resolved, and so far so good. 

The comp was running XP and I had a series of African safari pics on it as a screen saver. 

Now all that shows is a blank screen so is it possible to create a screensaver again with my pics?

Thanks for any replies?

Shenachie.

---

### Post by Ozymandias_117 on 2010-06-20
System -> Preferences -> Screensaver

You would probably want the "Pictures Folder" and place your pictures in ~/Pictures

---

### Post by fooman on 2010-06-20
"carousel" and "photopile" are nice as well.

---

### Post by Shenachie on 2010-06-20
That worked a treat on the primary account. 

However on the guest account the CD is not recognised at all. 

Suggestions please as unless the CD is "seen" I cannot copy over the pics into the pictures folder. 

Thanks

shenachie

---

### Post by ajgreeny on 2010-06-20
You did not mention a CD before so I'm not certain what you are trying to do.  The photos need to be in the Pictures folder of the user logged on, or linked from the main user to the guest user account.  The easiest way will be to link the /home/guest/Pictures folder to the primary user's /Pictures folder so the guest can read those photo files.  Come back if you need more info on how to do this.

---

### Post by Shenachie on 2010-06-20
More info please. :)

The pictures I want to use are burnt on a CD. When I put it in the drive using the primary account the icon appeared on the desk top and I was able to open the CD and drag the pics over to the picture folder. 

In the guest account, the CD is not recognised and so I need to link the two as suggested. 

Shenachie

---

### Post by ajgreeny on 2010-06-20
Firstly make sure the Pictures folder in the main user's home folder is readable by all.  Use a right click on the folder and go to Properties -Permissions tab and set it as shown in my screenshot, or use the command ```
chmod -R 755 /home/*username*/Pictures
``` username here should be the actual main username, not the word username, of course.

I assume the Pictures folder in the guest account is empty.  If I am right login as guest and delete that Pictures folder from nautilus.  

Now in terminal use the command ```
  ln -s /original/file /new/link
```  Example: 
   ```
ln -s /home/username/Pictures /home/guest/
```  Note that -s makes an "empty" file pointing to the original file/folder.  So if you delete the folder a symlink points to, you will be stuck with  a dead symlink (just [rm]("http://linuxreviews.org/man/rm")  it). 

You can also do this in nautilus when logged in still as guest by navigating to the main user's /home/username/Pictures folder and with the mouse middle button (scroll wheel) drag it to the guest home folder.  A menu will appear asking if you want to move, copy or link, so choose link.

All done.  The guest home folder will now have a Pictures folder linked to the main user Pictures folder and should be possible to let the guest screensaver Pictures Folder work as it should.

EDIT:
Sorry about the screenshot- I simply forgot to add it.

---

### Post by Shenachie on 2010-06-21
Sorry to say there is not screen shot at this end so that makes things a bit awkward to follow.

Further where do I find "nautilus"?

I am a very basic user sorry to say.

Shenachie

---

### Post by Scunnered on 2010-06-21
**Shenachie**

Any guest house using Ubuntu gets my vote. Do you have a web page?

---

### Post by k3lt01 on 2010-06-21
> **Shenachie said:**
> Further where do I find "nautilus"?Nautilus is like Windows Explorer. When you go to Places all the files and folders displayed are displayed in Nautilus.

Now as for your Screensaver it is actually quite easy but takes a little bit of patience to accomplish. Some will say there are much easier ways to do it but if you want ALL users to be able to use it WITHOUT giving everyone rights to the main user /home.

First thing you need to do is take a look at my signature and follow the process in the link on How To: Create a background slideshow. I'll post the rest of the process in my next post. I'm doing this so you can concentrate on the first part before working on the second part.

---

### Post by k3lt01 on 2010-06-21
Now you have your slideshow setup and in the right place you need to go to Places > Search for Files. Search for Cosmos and you will find cosmos-slideshow.desktop (a configuration file in /usr/share/applications/screensavers), cosmos (the folder containing the Cosmos backgrounds which you will have noticed is used as the basis of the slideshow background), and cosmos.xml (again used as the basis for the background slideshow).

Open cosmos-slideshow.desktop by opening a terminal and typing or pasting
```
gksudo gedit /usr/share/applications/screensavers/cosmos-slideshow.desktop
```.Now you have that open change the following *[COLOR="Red"]ITALIC[/COLOR]* entries to suit your screensaver.

```
[Desktop Entry]
Name=*[COLOR="Red"]Cosmos[/COLOR]*
Comment=Display a slideshow of pictures of *[COLOR="Red"]the cosmos[/COLOR]*
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=/usr/share/backgrounds/*[COLOR="Red"]cosmos[/COLOR]*
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver
```
Save the file with A NEW NAME, this is so you don't lose cosmos.

Now that you have done that press Alt-F2 and in the dialogue box type in gconf-editor. Go Apps > gnome-screensaver. On the oppsite pane you should see a list go down until you see "mode", tap on mode twice and you will get another dialogue box appear, enter single into the Value line and click ok. Open the Screensaver preferences choose you new screensaver and your done.

Be sure to log in on the guest account and select your new screensaver in the screensaver preferences so your guests can view your pictures.

Let us know how you go.

---

### Post by ajgreeny on 2010-06-21
> **Shenachie said:**
> Sorry to say there is not screen shot at this end so that makes things a bit awkward to follow.

Further where do I find "nautilus"?

I am a very basic user sorry to say.

Shenachie
Sorry about the screenshot.  I have now added it here and at the previous post.

---

### Post by Shenachie on 2010-06-22
[www.mortonhousehotel.co.uk](www.mortonhousehotel.co.uk) is the web site.

Thanks for your assistance and I got so far with gedit then fell at this hurdle. 

sudo cp /home/YOURUSERNAME/PathToYourFolder /usr/share/backgrounds
I have tried every combo I can think of but cannot get this code accepted where my user name is pete, and the folder is in the home folder and called Screensaver.xml

This is the trouble with being a newbie the more advanced users take a lot for granted and miss out steps that for us beginners are complete stumbling blocks.

I once lectured for two hours and after was approached and asked a question and then realised I had omitted a point and for some the rest of my talk was a waste of time as it was a critical point which I was so used to people knowing I just carried on..... oops..

Pete

---

### Post by k3lt01 on 2010-06-22
> **Shenachie said:**
> [www.mortonhousehotel.co.uk](www.mortonhousehotel.co.uk) is the web site.

Thanks for your assistance and I got so far with gedit then fell at this hurdle. 

sudo cp /home/YOURUSERNAME/PathToYourFolder /usr/share/backgrounds
I have tried every combo I can think of but cannot get this code accepted where my user name is pete, and the folder is in the home folder and called Screensaver.xml

This is the trouble with being a newbie the more advanced users take a lot for granted and miss out steps that for us beginners are complete stumbling blocks.

I once lectured for two hours and after was approached and asked a question and then realised I had omitted a point and for some the rest of my talk was a waste of time as it was a critical point which I was so used to people knowing I just carried on..... oops..

PeteHi Pete

I understand what you mean. I'm a teacher by profession and a motor mechanic by trade, I am used to getting in amd figuring things out and then just typing it up as I worked through it not thinking (sometimes) that it is all a lot of gobbledygook to most people.

Having said that we have 2 ways to go around this. IF you want to continue on that path I'll work through it with you no worries but I will need your help with screenshots of locations. 

Another and more simple option which I didn't find until today, simply because I look for the native style setup and not the staring me in the face setups, is - open Fspot (Applications > Graphics > Fspot photo manager), find the pics you want to use > mark (tag) them as favourites > open Screensaver preferences (Go to System > Preferences > Screensaver) in the left hand pane find Fspot photos and click it then click Preview. If it works, which it should, you should be seeing a preview of you pics as a screensaver.

Make sure you go through that process in the "Guest" account.

---

