---
title: "NVIDIA -How to get drivers ?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by rufio666 on 2010-08-04
Hi there !
I need help with drivers for GeForce 7600GS Silent/HTD/256MB Asus brand.Should i remove xorg drivers for ATi before GeForce will be installed ?

---

### Post by 23dornot23d on 2010-08-04
I would think that would be a good idea .... to remove the ATI drivers first ,

Once the new card is installed it should go in in ok without acceleration ..... then you just need to go to hardware drivers to update them.

And add the current Nvidia driver.

Hopefully all will go well .......

Check my links below for any known problems ......

Just for information ..... might be worth printing the relevant bits off before hand ...... 
just in case anything should go wrong.
best safe than sorry so to speak .....

---

### Post by phazixc on 2010-08-04
I'm Running:-

Toshiba q505 888

Ubuntu 10.04 lucid 64Bit

Core 7i q740
Nvidia Gts 360m 1gb
4 Gb Ram 


I Updated to 256.35 = Excellent / perfect

Then my updates from X-swat and Xorg Egders updated to 256.44 this = my world falling apart.

My system completely locks up / hags / kills its self within 4 mins of logging in. 

If I load anything I.E wine to run a game. 

It really doesnt like that... My problem is i'm only a year into ubuntu and I have done manual updates before, but what im doing isnt working as I have tried purge remove nvidia .44 and disabling the two ppa's then manually installing .35 ..

BUT

when I start the gdm = great it works, then when I restart = not great....because I'm on failsafe graphics and the x sever setting not in menu (if it is in menu then theres nothing in there; apart from that msg to restart X) and when I load Hardware drivers the nvidia card isnt there..

I would like to think that some of your reading this are laughing because you are what I would call a pro in the ubuntu area and that you could / will post a detailed step by step to help me install .35 through the x-swat or x-org egder ppa or even manually download it and install it that way, so when I restart it works, and more to the point I can keep those two ppa's in my system so when i hit the update button I can see ubuntu wants to update to .44 which I WONT DO....

One year into ubuntu and I haven't logged into windows since.

As I find theres always someone will to help fix something in ubuntu..

anyway thats that, Mr/Mrs pro.... can you post that guide please.

P.S im currently on Linux-x86_64 NVIDIA Driver Version: 195.36.24 Server Version Number: 11.0 and Server Vendor Version: 1.8.2 NV-CONTROL Version: 1.22
gnome 2.30.2 and kernel linux 2.6.32-24 generic
platform X86_64



Thanks

---

### Post by 23dornot23d on 2010-08-04
This is all I usually do to get the Nvidia Drivers working  .... [LINK]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/")

______________________________________________


I currently run the 256.35 = Excellent / perfect one too .....

was after the later one .... [256.44]("http://www.nvnews.net/vbulletin/showthread.php?t=153575") ..... but not added it yet .... seems like a pre-release here.

Usually you can just pick the ones you want ,, within Synaptic
as long as you have purged all the old stuff and also have the current kernel and headers installed
the version will usually builds with the Nvidia driver you have picked ...... 

are there any [bug reports this is all I found wine]("http://permalink.gmane.org/gmane.comp.emulators.wine.user/67591") .. seems relatively new ... sometimes they give more information as to why its happening.

[COLOR=Red]Go to the [Thread you have opened to reply]("http://ubuntuforums.org/showthread.php?p=9678589#post9678589") ...... ( as this is rufio66 's thread - otherwise it will confuse things )[/COLOR]

---

### Post by phazixc on 2010-08-04
thanks ill check it out now thanks again

the only thing with that link is it say to add PPA x-swat I have that but when i run the update all it want to do is install 256.44 not 256.35.

how do i get 256.35 on my system through the ppa cannt I..

also would   


sudo apt-get purge remove nvidia-* 

work to completely remove nvidia drivers and how do I update the kernel and header


thanhks

---

### Post by rufio666 on 2010-08-04
Ok than .There is xorg driver ,kernel module and some Transitional package for nvidia 185 on repo .Instal xorg as first and after than nvidia 256.44 ? and very important haw to install already downloaded nvidia 256.44 drivers (open terminal and ...?)

---

### Post by 23dornot23d on 2010-08-05
@ rufio66

You just need to go to 

**System Administration -hardware drivers** ........  to update.

(you only need to do this once)

And choose / add the **current Nvidia driver**.

if the graphics are working ok

Then look at 

**System Administration - **Nvidia X Settings ........ and do a screenshot ,,,,, and post it please.

And choose / add the current Nvidia driver.

That should be enough to get the drivers you need rufio66 ......
Have you got the new card in and your graphics working now ?

 [COLOR=Red] You do not need to use the 256.44 ? ( Thats a totally different issue for phazixc )[/COLOR]

---

### Post by rufio666 on 2010-08-05
Hi there everyone !
I have just solved all thing with nvidia drivers in your way and it works !
I'm ready to insert some screenshot but i never did an url of any image before(it's not simple "upload image")Anyway i'm ready to post it but help with this simple url coding is needed.
Thank you for help everyone !

---

### Post by 23dornot23d on 2010-08-06
[B]I am glad that its working ok.
[/B]

When I post images ...... 

First of all  take your screenshot ...... press F13
( one more thing .... resize the image in GIMP or you favorite photo editor to 800 x 600 or slightly smaller )

or load ksnapshot .... I like this for just choosing a region ...... of the screen .......
and then pick a region on the screen to copy and save jpg's are best smaller file size for uploading and for viewing.

________________________________

I use Tinypic [http://tinypic.com/]("http://tinypic.com/usermedia.php?uo=XAS1fUiO8rDuN5A%2Bt1I6Xoh4l5k2TGxc")
or[ Imageshack]("http://imageshack.us/") is another one


Go to the Tinypic site ...... use Browse ....... and find the screenshot.png
it should be in your Desktop or Home directory.

Choose it .... upload it ...... 

then copy the link on the tinypic site - **Direct link for layouts**

Choose the icon on the top of here in the text editor that looks like a mountain on a yellow background ......

and paste the direct link into it.


Your screnshot will show on here then .....

---

### Post by rufio666 on 2010-08-07
Thank You for "haw to"upload images !

---

### Post by phazixc on 2010-08-16
Yeah I have decided to stay with 195 as 256.44 is unstable on my system


!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Qosmio X505


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes

---

