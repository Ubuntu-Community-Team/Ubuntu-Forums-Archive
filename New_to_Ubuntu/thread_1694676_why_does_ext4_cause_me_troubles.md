---
title: "why does ext4 cause me troubles?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by whiteman on 2011-02-24
I am not that new to ubuntu. been with it since 8.04. I installed it in my xps400 when it refused to let me reinstall installation disk.(winxp)
I have several machines around the house and my wife works a sys analyst for a major credit card company and it is necessary that our lan perform.
no problems thru jaunty. everybody could trade files, print. this is with Mac osx, MacBook, mac mini, two win doze laptops, and VPN. using windoze xp and win7. in fact. the windows had no problems wit the lucid even.
 the snag came up with when I went to karmic. my canon printer was missing. it was showing as a drive? maybe it was ext4. i used turboprint which costs, and was ok, but when I went to lucid, even turbo print couldn't detect canon printer. drivers are no problem. drivers I can find. gutenprint has millions that work. but when I would go to add a printer....there wouldn't be anything there, only other. my hp printers would show up. then there was the cups thing. my cups id and password wouldn't work from remote. the other day when I tried to share files with my ubuntu, using lucid...it wouldn't recognize my password. my password is just zzzzzz. that's it, 7 zs. can't mess that up. so for the umpteenth time i installed jaunty.I should mention here that I had to put a new motherbd in this Dell ubuntu, so I didn't wanna give up.
How can I get jaunty to be upgradeable. I have grown used to using handbrake,and several other add ons in firefox that aren't available with jaunty.
ok ok. I cN hear it already."quit being a whiner" or we don't have problems with upgrading to lucid, meerkat etc. I would love to use lucid. btw when i installed meerkat, I got a black dos type screen. no gui at all? so i can't honestly say that it was screwed up for me. but I have installed at least ten flavors of. Linux and always got some kind of gui. this looked like DOS.
is there a way to keep ext3, and just keep up my sources.list? is such a thing possible?
I don't understand why jaunty works so much better for me than any of these "improvements". is it ext4?

---

### Post by LowSky on 2011-02-26
EXT4 has NOTHING to do with applications not working correctly. EXT4 is just a type of formating option for the hard disk. You can specifically pick a number of them including the older EXT3 during an installtion if you pick manually to format the drive.

Also your post is very confusing, First you mention 8.04 (Hardy Heron) then you say Jaunty, otherwise known as Ubuntu 9.04 (Jaunty Jackalope), then you say no problems with Lucid, Ubuntu 10.04 LTS (Lucid Lynx). Then you say the snag occured when you went to Karmic, known as Ubuntu 9.10 (Karmic Koala). Why would you downgrade?

You mention a Canon Printer but don't mention which model, can we have that please, and how is it connected?

CUPS needs to be reset up when you do a full install. Upgrading does not affect it's performance, but a fresh install will wipe out a CUPS server.

You shhould never give out password information. ANd when you do a completly new install again settings are gone and need to be redone.

Why did you go from Lucid to Jaunty?
Installing a new motherboard can effect things like IP addresses especially if you are running things like network printers.

Why not use Ubuntu 10.10 (Maverick Meerkat) or 10.04 LTS?, the black screen you mention can be from a number of things, and we know how to fix those issue usually pretty well. Its also more secure and can use the newest versions of drivers and applications like Firefox and Handbrake as you mentioned.

Like I said you can kep EXT3 but it doesn't matter. The Source.list will need to go, sorry but editing it really isn't an option.

---

### Post by whiteman on 2011-04-13
Low Sky...its been awhile but my Ubuntu machine died and I had to replace the motherboard. Thats done and Im back to this.
OK sorry for confusions.
I said 804.....MY FAULT. The last  one I have goodluck with is Jaunty, whatever number that is. I thought it was 9.04.
The printers Im using are....HP 930.....another HP i forget the number and the Canon MP 470 Pixma.
OK the HPs are neither here nor there. THEY WORK fine with all distributions.
I have tried clean installs, upgrade(from within Jaunty) formatting HD and installing(most recent with new motherboard). I tried to install 9.10 using a disk sent to me by ubuntu(i guess) this website offers free disks. Everything went fine, except when I go to ADD PRTR....there is no canon there. Its not a matter of drivers, the driver is downloaded and installed with Gimp-Gutenprint..whatevr. ITS THERE. I can see the driver in the dir with all the other ones.
If I click on computer....I am shown a strange thing.(This is why I think its a formatting issue) It misreads the canon as a drive. There on the screen is my external drives.....File system, HOME, etc etc cd roms(2 of them) AND......a Hard drive called Canon MP470???Now this printer has some sort of usb outlet for printing, I have never used it.
MY HPS, are shown under printers. One thing I have noticed is this.....once you istall a printer it is gone from this dialogue box(ADD PRINTER) In other words if you have an HP printer and you click on ADD Printer....the next time you attempt to ADD Printers..the HP will not be available. SO this makes me think that the system "thinks" that the Canon is already installed because it is listed as a DRIVE.
I DONT KNOW.
I DO KNOW THIS. Jaunty is ext3. 910 is not. I can use my printer with Jaunty, I cant with 9.10. I have nothing else to figure.
What else is different? Now there is a way that Canon MP470 can be made to print with 9.10, 10.04, etc...using an app called Turboprint. But is is not free. It cost 29 bucks and it acts funny with CUPS. SOmetimes. I get backend probs, authenication issues.
If I could disable this thing that causes the Canon to show up as a drive I would be home free. I want to upgrade!! I like being able to use my iphones, Handbrake, airplaying, and all the other great things I can do with Lynx. But I am not the only one who uses this Lan...and my wife uses the Canon for her Job. Because of space constraints it is neccesary to hook pronters up to the Dell(Ubuntu).
WHAT IS CAUSING THIS? IF IT AINT THE ext4?? Thats is the only thing that is different to me and that Lynx,10.10, 9.10 etc etc have in common that Jaunty doesnt have.
I am open to all suggestions within reason. I dont wanna admit defeat, go back to windoze.

---

### Post by whiteman on 2011-04-13
I missed somethings first time. I realize settings ect change. I downgraded because(Lucid to Jaunty) Because I missed being able to print! I am not new to this. I have been using Linux since mid 90s. II know how to setup add printers, reset cups, edit smb.conf, cups. etc etc. I am not beating my chest here, I only wanna let you know what level of learning or ignorance I am at.<g> And passwords...I could care less. Whats that gonna get uyou? You cant get my net without my wpa info. But I am open to any serious suggestions you may have unless you feel like you cant help. A person will downgrade anytime they are trying to retrace their steps. Its not that unusual. I have been using Jaunty for two years now and much of it cant be upgraded now. Its pretty much obsolete.  I have been recompiling a lot of stuff just to keep it. BUT ID RATHER UPGRADE. But it has caused me so many problems it hasnt been worth it. I dont recall ever seeing an option to keep ext3 when upgrading. I thought ext4 was pretty much a  feature of 9.10, not an option. I could be wrong. Where does this happen?

---

### Post by walt.smith1960 on 2011-04-13
I doubt drive formatting is causing your problem. Does your device have a card reader? If so, perhaps that's what is showing up as a drive.  I looked on openprinting.org and didn't find the MP470 but MP450, MP480 & MP490 are listed.  People there are using drivers for similar models e.g. using the MP490 software with an MP 480.  What do you see when you click System -> Administration -> Printing.  Is the Canon listed? Anything interesting when you right-click the printer icon then properties?

---

