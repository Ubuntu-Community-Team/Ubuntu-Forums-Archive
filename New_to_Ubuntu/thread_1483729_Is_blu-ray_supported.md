---
title: "Is blu-ray supported?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-14
So I decided to build a cheap media computer under $500, but that was beyond me because I don't really know the bare minimum I would need, so luckily I came across this.

[http://www.amazon.com/Acer-AX1301-U1312-Desktop-PC-Black/dp/B0031RG3AU/ref=sr_1_3?ie=UTF8&s=pc&qid=1273889551&sr=1-3](http://www.amazon.com/Acer-AX1301-U1312-Desktop-PC-Black/dp/B0031RG3AU/ref=sr_1_3?ie=UTF8&s=pc&qid=1273889551&sr=1-3)

And I plan on replacing the optical drive, or if it has a second port with this blu-ray drive

[http://www.amazon.com/LITE-Blu-ray-Internal-Optical-iHOS104/dp/B002EE996Q/ref=sr_1_1?ie=UTF8&s=pc&qid=1273886784&sr=1-1](http://www.amazon.com/LITE-Blu-ray-Internal-Optical-iHOS104/dp/B002EE996Q/ref=sr_1_1?ie=UTF8&s=pc&qid=1273886784&sr=1-1)

I don't want to use Window's media Center because from what I understand it's a bit unstable still. I'm going to have this hooked up to my TV via HDMI and I could rearrange the desktop so my dunderheaded parents could figure it out without having to call me in to tell them how to use the DVD player every day.

I want to make it where once they pop in the disc it's playing if full screen without having to do anything. Currently we own the Hangover, Batman...the most recent one, Avatar, and Inglorius Basterds. We usually play them on our PS3 but I don't want to drag it around anymore.

While we're at it, is it possible to use the netbook edition of ubuntu to work on a normal PC? I like how the main menu is organized, and it would work perfectly for my Media computer.

---

### Post by 2hot6ft2 on 2010-05-14
[Playing Blu-Ray and HD DVD Video]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

Installing MakeMKV

Download both of these and save them to your Downloads folder
[MakeMKV Binaries download]("http://www.makemkv.com/download/makemkv_v1.5.5_beta_bin.tar.gz")
[MakeMKV Source download]("http://www.makemkv.com/download/makemkv_v1.5.5_beta_oss.tar.gz")

then
Go to
Places > Downloads
Right click on them both one at a time and select Extract here, then
Open a terminal
Applications > Accessories > Terminal
and run these
```
sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev
```
```
cd ~/Downloads/makemkv_v1.5.5_beta_oss
```
```
make -f makefile.linux
```
it will take a while so wait for it to return to the prompt which will end with
makemkv_v1.5.5_beta_oss$
```
sudo make -f makefile.linux install
```
```
cd ~/Downloads/makemkv_v1.5.5_beta_bin
```
```
make -f makefile.linux
```
That brings up the terms of use. Use the down arrow key to scroll thru them to the bottom and hit the q (Q) hey to return to the terminal. Type in yes and hit Enter to accept them.
```
sudo make -f makefile.linux install
```
All done installing. Now you can start it with
```
makemkv
```
It doesn't create a menu item for it so to create one.
In the top left panel next to Applications
Right click on the Ubuntu Logo and select Edit Menus
In the left side select Sound & Video and click anywhere in the right side.

On the right click on New Item
Fill it in like this
Type: Application
Name: MakeMKV
Command: /usr/bin/makemkv
Comment: Can be whatever you want like DVD Ripper

You can click on the launcher picture and pick another one of your choice.
Click OK
All done now it's in the menu in
Applications > Sound & Video > MakeMKV

Have fun
:guitar:

---

### Post by Legendary_Bibo on 2010-05-14
Will it work as newer titles come out?

and will it be where the disc shows up and my parents just have to click on it then bam! it plays?

I know blu-ray has some sort of character encoding DRM protection (AACS?) Would it be able to update my blu-ray drive's firmware?

---

### Post by 2hot6ft2 on 2010-05-14
> **Legendary_Bibo said:**
> Will it work as newer titles come out?

and will it be where the disc shows up and my parents just have to click on it then bam! it plays?

I know blu-ray has some sort of character encoding DRM protection (AACS?) Would it be able to update my blu-ray drive's firmware?
Beats me but you could try reading the link at the top of the post.
Personally I agree with the link at the bottom of that page and don't use or buy Blu-Ray.

[Why you should boycott Blu-ray and HD-DVD]("http://bluraysucks.com/")
:popcorn:

---

### Post by Legendary_Bibo on 2010-05-14
Hmmmm...I think I have a better idea. I can install ubuntu on the media PC, and the blu-ray drive on my dad's PC and rip the blu-rays and transfer them over to the media PC. I planned on just putting our whole Video, Music, Picture collection on it. Also to set it up as a DVR if possible...I'll probably have to install another hardrive in the future if possible.

---

### Post by Ozymandias_117 on 2010-05-14
> **2hot6ft2 said:**
> Beats me but you could try reading the link at the top of the post.
Personally I agree with the link at the bottom of that page and don't use or buy Blu-Ray.

[Why you should boycott Blu-ray and HD-DVD]("http://bluraysucks.com/")
:popcorn:

Wow, that s**t is crazy. I can't believe people actually ALLOW Hollywood to do stuff like that.

---

### Post by 2hot6ft2 on 2010-05-14
> **Ozymandias_117 said:**
> Wow, that s**t is crazy. I can't believe people actually ALLOW Hollywood to do stuff like that.
[-( And yet they still line up to buy it.[-(

---

