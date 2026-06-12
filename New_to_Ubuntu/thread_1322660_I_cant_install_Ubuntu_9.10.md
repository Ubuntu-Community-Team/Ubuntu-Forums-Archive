---
title: "I cant install Ubuntu 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by whitey_1 on 2009-11-11
Hello everyone,

Im sure you have seen this question 1000s of times before, but i have looked through this forum and other sites and cant seem to find the answer to my problem. I am a complete newbie to this ubuntu, but it looks really good, so heres the situation..

I downloaded the Ubuntu 9.10 from this link:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I clicked the green button, 'begin download ubuntu desktop 9.10 (32 bit)'

I burned the iso file (ubuntu-9.10-desktop-i386.iso) to a cd-r using the program 'InfraRecorder' using the instructions as stated on this page;
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

But, i put the cd in, restarted the computer, all seemed to go well up to a point. It asked me which language i want, that was fine, then after that nothing happened. It had the little circular logo flash for abit, then the screen went black, and the computer restarted to do the same thing.

*my computer stats*
cd/dvd drive - primary
Win xp home ed - sata hd - secondary
IDE hd - (Blank) - third

I did try the WUBI program, it did the same thing as the other way i stated earlier.

Please can someone help, sorry for the long messege, i hope it is all relevent detail

Thank you


ps
I did try the 'check disc for defects' option from the ubuntu menu when the pc restarts, and it reported 1 file had an error. I also tried this on my laptop, same problem there. But i did download it from the main website! so im confused

---

### Post by marcopolo1981 on 2009-11-11
Did you verify the md5 hash of the iso you downloaded against the one from here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) ?

The one you should be checking is under 9.10 and reads

3faa345d298deec3854e0e02410973dc         ubuntu-9.10-alternate-i386.iso


It should read EXACTLY: 3faa345d298deec3854e0e02410973dc

---

### Post by marcopolo1981 on 2009-11-11
From your Windows, go to [http://www.killertechtips.com/2008/05/25/how-to-view-check-md5-checksums-in-windows/](http://www.killertechtips.com/2008/05/25/how-to-view-check-md5-checksums-in-windows/) and download hashcheck. Once installed, right click on the iso file, click properties, then file hashes

---

### Post by whitey_1 on 2009-11-11
Thanks Marcopolo,

I Downloaded hashtab, searched for the file under the file name, it came up with this

MD5 Sum:
8790491bfa9d00f283ed9dd2d77b3906

so it doesnt compare with the 3faa345d298deec3854e0e02410973dc

Im confused, does that mean the file i downloaded is wrong?

please help, thank you

---

### Post by soapytheclown on 2009-11-11
Try and redownload the cd,

You should be aware that with downloading theres possible problems with data packets being lost and creating a 'corrupt' file. Thats a standard problem with any networking system unfortunately :(

---

### Post by whitey_1 on 2009-11-11
I notice on here it says in a green box to consider downloading it using bittorrent, is that my next step do you think?

Its strange, i cant see why the link on the main page of the website would offer a corrupted version of Ubuntu, if it is that , then i will have to download it using a torrent.

What do you all think about this ?

---

### Post by halitech on 2009-11-11
Actually the MD5 Sum for the DESKTOP cd is

[color="red"]8790491bfa9d00f283ed9dd2d77b3906[/color] ubuntu-9.10-desktop-i386.iso

so the MD5 Sum is fine but the fact that you have 1 file with an error indicates you have a bad burn. I would suggest using bittorrent to do your download as it checks the file as you download and will redownload a corrupt piece if required. Of you can try to reburn the iso, making sure you use the lowest possible speed.

---

### Post by whitey_1 on 2009-11-11
i have found a list of torrents available on this page:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

The relevant torrents on this page are;

Ubuntu 9.10

    * ubuntu-9.10-alternate-amd64.iso.torrent
    * ubuntu-9.10-alternate-i386.iso.torrent
    * ubuntu-9.10-desktop-amd64.iso.torrent
    * ubuntu-9.10-desktop-i386.iso.torrent
    * ubuntu-9.10-server-amd64.iso.torrent
    * ubuntu-9.10-server-i386.iso.torrent
    * New: IPv6 only torrents for users of IPv6 (learn more about IPv6)


Am i right in thinking i need the  * ubuntu-9.10-desktop-i386.iso.torrent

My computer is a pc, 32 bit architecture.

Thank you for all your help so far

---

### Post by marcopolo1981 on 2009-11-11
Apologies for giving the wrong md5.
I assumed you had downloaded the alternate iso due to you saying everything was fine until you select the language. My bad.

---

### Post by halitech on 2009-11-11
If you are sure you want to install it and you don't need anymore time to test it, I would go with the alt install cd for i386.

---

### Post by ricardo.gloe on 2009-11-11
It's not the the website is offering a corrupt version. What happens is that while downloading the file, there may be data transfers that end up going wrong, and you end up with a downloaded version of the file which is not 100% the exact copy of the original file, hence an "imperfect" copy. That's why you compare the md5 hash to see if the download went smoothly or not. 

It can happen to any file, the larger the file, more risk of these error occurring.

The bittorrent reccomendation is simply because the main download locations/servers are subject to increased use these days, as everybody's downloading Ubuntu 9.10 KK, and the torrent options were downloading faster. 

Again, choose a download source (either from the website or a torrent), check md5 hash before burning and if it's ok, then you shoull have no problems installing.

---

### Post by soapytheclown on 2009-11-11
EDIT:
ricardo.gloe has just explained all this but i spent time writing this so its not going... :)

/EDIT

I think I havent explained myself so well,

The CD image is fine to download, when you download a file (any file) over the internet its sent in parts AKA packets. By random chance theres always a tiny chance packets will get lost. 99% of the time if this happens your computer will request to have that packet sent to you again. If for some reason (which is what i think has happened to you) it just plain wont request a resend (essentially so that packet is just not in your download) and as such you end with a corrupted download.

If your not charged for bandwidth usage then I suggest you try and redownload the CD again as you did - perhaps use another nearby server?

If you already run torrents you could get it Via that if you wish.

---

### Post by whitey_1 on 2009-11-11
Thank you for the info on the burn speed, i read that x4 is a good speed, and use a cd-r disc is best?

 i am downloading this torrent at the moment;
ubuntu-9.10-desktop-i386.iso.torrent

---

### Post by whitey_1 on 2009-11-11
Is there anyway of downloading that Ubuntu without using a torrent

Ive never had any luck with torrents, it is downloading at less that 10 kbs


Can someone help me with this, not the whole torrent speed thing, i dont want to be trying to do that port fowarding again, just want a working ubuntu iso file

Please can you help?

---

### Post by soapytheclown on 2009-11-11
Okay, after reading peoples posts again. First of all ignore what we've said about that ISO being corrupt. (It does happen, but in your case your ISO is fine). The problem you face soley is the fact that your CD was 'mis-burnt' If you have that ISO still, just reburn it again - generally the slower you burn the lower the chance of a write error - but just to be sure do a data verify on your disc (most burning software has this option) to be 100% sure. Hopefully this way you shouldnt get that one error.

---

### Post by whitey_1 on 2009-11-11
Hi Soapy and everyone,

I have tried many times now with new cds, burning it as slowly as possible etc, still no luck, and still exactly the same problem, an error on 1 file.

The slowest i have been able to burn a cd at is 10x, but it is still not working,

it stops after i selected the language, and if i check the disc for errors, 1 file error is always found.

My problem hasnt changed at all since the start of this question, can someone please help?

---

### Post by whitey_1 on 2009-11-11
Cant anyone reply to this anymore? as far as i can see, its a simple situation

---

### Post by whitey_1 on 2009-11-11
I have already invested hours of my time trying to solve this

Messege to Unbuntu, if you want people to move over from windows - youll have to make it abit simpler than this! Because those instructions on the main page are wrong in my experience

---

### Post by witeshark17 on 2009-11-11
Maybe it was a bad CD burn. That happens rather a lot. I might try using the terminal wget command for the nearest download mirror

---

### Post by whitey_1 on 2009-11-11
Ive already been trying to reburn it, but it wont work still.

The programs suggested to burn an iso disc do not burn it at x4 speed, minimum of 10 speed on those programs,

i am trying brasero and k3b, but how am i supposed to install those things, theres no exe


can someone please help here, this is getting stupid now

---

### Post by halitech on 2009-11-11
When you check the disk, is it always the same file that is corrupt? 

You don't install using .exe files like you do in windows, you use Synaptic or apt-get install from the terminal.

I'm starting to think if you are consistantly getting bad burns, either the cds are crap or your burner is dying. Do you have a different brand of cd you can try or a different computer with a burner you can try to burn the cd?

---

### Post by whitey_1 on 2009-11-11
> **halitech said:**
> When you check the disk, is it always the same file that is corrupt? 

You don't install using .exe files like you do in windows, you use Synaptic or apt-get install from the terminal.

I'm starting to think if you are consistantly getting bad burns, either the cds are crap or your burner is dying. Do you have a different brand of cd you can try or a different computer with a burner you can try to burn the cd?


thank you ,

I have been trying 2 different types of cd, ive been burning them on my laptop. The laptop has burned other cds fine, no probs.

Is the speed at which i am burning them the problem? ive not been able to burn them at anything less that x10 , i know its suggested that i burn them at x4 , but i cant find a program that will do it at that speed. 

I did try imgBurn, i was able to select x4 burn speed, but it had an error and said it had to burn it at x12


Is it me, or is this ridiculas now.

---

### Post by durand on 2009-11-11
What type of computer are you running it on? Some laptops have problems booting ubuntu cds...

---

### Post by Merk42 on 2009-11-11
If you have a USB drive you may be able to use [UNetBootin](http://unetbootin.sourceforge.net/) instead of burning CDs.

---

### Post by whitey_1 on 2009-11-11
> **Merk42 said:**
> If you have a USB drive you may be able to use [UNetBootin]("http://unetbootin.sourceforge.net/") instead of burning CDs.

Im just going to try that now, just as you said

thank you

---

### Post by whitey_1 on 2009-11-11
No, ive just done that, all as instructed, and it didnt work,

i restarted the computer with the flash drive in already, booted off it, and 3 options appeared 'default, help, oem' - all of them lead to the computer just restarting.


I am trying to download a new iso file, but people on here seemed to agree the iso file was fine?! 

im am totally stuck now, and after hours im no further  with this problem.


Someone please help?

---

### Post by Gael33 on 2009-11-11
> **Merk42 said:**
> If you have a USB drive you may be able to use [UNetBootin](http://unetbootin.sourceforge.net/) instead of burning CDs.


I had a similar problem with my older computer. I wiped the hdd clean and cleared the CMOS ... booted from the CD-R (Ubuntu 9.10 iso burn) and got an error message half way through the install. The message read; I/O ERROR on Install Disk. I was advised to burn the disk again using a lower speed 4X and it worked. Word of advice, don't use cheap and cheerful CD's and DVD's ... go for a good quality disk and maximise your chances of success. Disk problems can be irritating and time consuming.

---

### Post by whitey_1 on 2009-11-11
> **Gael33 said:**
> I had a similar problem with my older computer. I wiped the hdd clean and cleared the CMOS ... booted from the CD-R (Ubuntu 9.10 iso burn) and got an error message half way through the install. The message read; I/O ERROR on Install Disk. I was advised to burn the disk again using a lower speed 4X and it worked. Word of advice, don't use cheap and cheerful CD's and DVD's ... go for a good quality disk and maximise your chances of success. Disk problems can be irritating and time consuming.

I shall try that next, but my discs are not cheap, they are cd-r as was advised on the ubuntu website

thank you, but this is not the answer to my problem

Can someone offer me any help please

---

### Post by user333 on 2009-11-11
Well, I agree, whitey_1, With what you quoted. You have a defective disk, and you can't do much about it. I had the same problem an you, just with 9.04. I just burned another disk and everything was fine. Cheep and plain disks work great for me, though :) I don't entirly agree.

---

### Post by whitey_1 on 2009-11-11
> **user333 said:**
> Well, I agree, whitey_1, With what you quoted. You have a defective disk, and you can't do much about it. I had the same problem an you, just with 9.04. I just burned another disk and everything was fine. Cheep and plain disks work great for me, though :) I don't entirly agree.
  thank you

I would like it to be the discs, but i am using 2 different brands of cdr, ive tried 3 different machines, 2 iso downloads,  tried booting it off of usb - no luck on anything


im stumped as what to try next, can someone help me with this, much appreciated if you can please

Is it all down to me needing to get the iso from bittorent? because that thing downloads at an extremely slow rate (less that 10 kbs)

---

### Post by William Anderson on 2009-11-12
Hi, 

You know, do the Ubuntu cds that you have burnt fail to boot on all three computers that you have used to burn with? 

If it is failing on one computer (the one that you want to install onto of course) it may be that the cd rom drive on that computer is failing to properly read the disk. I have had the situation where I could burn a disk, have the burning software verify the disk, be able to run md5sum on the cd device file successfully (and get the correct checksum value) but was not able to read files correctly from a part of the disk. 

I may be fighting this kind of issue on my laptop as I have done all this on the 9.10 alternate cd that I wish to upgrade from (to save bandwidth), but the upgrade process complains about corrupt files and aborts.

I know that this does not help much, but in my experience Linux is much more picky about the condition of the hardware that it is running on and will not tolerate marginal hardware that seems to work ok in Windows.

Also, if the iso image gives you the correct md5sum value for the image that you are using, you have a good image and do NOT need to download another copy. Given the md5sum that you posted in an earler message and that you are using the i386 desktop version, you have a good image. Will the software that you are using allow you to take an md5sum of the disk after you have burned it? In Ubuntu you could say "md5sum /dev/scd0" at a command prompt and have it calculate a checksum of the disk. The result should be exactly the same as the iso image file checksum. 

William

---

### Post by Gael33 on 2009-11-12
> **whitey_1 said:**
> thank you ,

I have been trying 2 different types of cd, ive been burning them on my laptop. The laptop has burned other cds fine, no probs.

Is the speed at which i am burning them the problem? ive not been able to burn them at anything less that x10 , i know its suggested that i burn them at x4 , but i cant find a program that will do it at that speed. 

I did try imgBurn, i was able to select x4 burn speed, but it had an error and said it had to burn it at x12


Is it me, or is this ridiculas now.

Whitey, Am I right in thinking that you still haven't managed to burn a CD-R at x4? Because if this is the case, you are just repeating yourself. Nerolinux and k3b both burn at x4 ... as I said previously, I had no luck at all until I managed to burn a disk at x4. One more thing, your reader may be misreading the disk because of a foreign body on the lens, clean the unit with a disk cleaner. It may do the trick, it certainly won't do any harm.

---

### Post by Annigma on 2009-11-12
Hi Whitey ):P

I'm an Ubuntu newbie too, having only dabbled a bit. I've also ended up with a download I'm not sure about, so I'm reading around, and stumbled upon your thread.

Just a couple of thoughts. Is everything fine with your HDDs? Have you done chkdsk, defrag, that kind of thing?
Have you tried running Ubuntu in Live mode? the option where no changes are made to your PC? Does it work on any of the machines you have access to?
My other thought was to buy a copy of Ubuntu. I got Feisty and Hardy from ebay. Cheap and quick (then you'll know it's not your dl that's the problem)

You've probably tried most of this, but I wanted to try and help, as I know how you feel :)

Good luck

---

### Post by whitey_1 on 2009-11-12
> **William Anderson said:**
> Hi, 

You know, do the Ubuntu cds that you have burnt fail to boot on all three computers that you have used to burn with? 

If it is failing on one computer (the one that you want to install onto of course) it may be that the cd rom drive on that computer is failing to properly read the disk. I have had the situation where I could burn a disk, have the burning software verify the disk, be able to run md5sum on the cd device file successfully (and get the correct checksum value) but was not able to read files correctly from a part of the disk. 

I may be fighting this kind of issue on my laptop as I have done all this on the 9.10 alternate cd that I wish to upgrade from (to save bandwidth), but the upgrade process complains about corrupt files and aborts.

I know that this does not help much, but in my experience Linux is much more picky about the condition of the hardware that it is running on and will not tolerate marginal hardware that seems to work ok in Windows.

Also, if the iso image gives you the correct md5sum value for the image that you are using, you have a good image and do NOT need to download another copy. Given the md5sum that you posted in an earler message and that you are using the i386 desktop version, you have a good image. Will the software that you are using allow you to take an md5sum of the disk after you have burned it? In Ubuntu you could say "md5sum /dev/scd0" at a command prompt and have it calculate a checksum of the disk. The result should be exactly the same as the iso image file checksum. 

William

Thanks William,

I have tried installing it on all 3 computers though, so i do know its not how its being read on a cd/dvd drive.

The Md5sum checked out ok, so that bit is ok.

The thing im not sure about is how to burn it at 4x speed, ive tried with many programs, and its not worked. Usually on these iso burner programs the lowest speed ive found selectable is 10x. There was one image burner where i was able to select 4x speed, but i tried it and it failed and reported that the cd had to be burned at 12x speed.

The speed could be the last part of the problem maybe?

---

### Post by whitey_1 on 2009-11-12
> **Gael33 said:**
> Whitey, Am I right in thinking that you still haven't managed to burn a CD-R at x4? Because if this is the case, you are just repeating yourself. Nerolinux and k3b both burn at x4 ... as I said previously, I had no luck at all until I managed to burn a disk at x4. One more thing, your reader may be misreading the disk because of a foreign body on the lens, clean the unit with a disk cleaner. It may do the trick, it certainly won't do any harm.


Thank you for your reply,

It is not my intention to repeat myself, i am just trying to work through a problem by eliminating the possibilities. The cd burn speed does seem relevant, so i am trying to work through that problem. 

I am welcoming all the help the people of this forum have given me so far.

If any one else knows this problem could be due to another factor that i have yet to try, please add to this discussion.

Thank you

---

### Post by whitey_1 on 2009-11-12
> **Annigma said:**
> Hi Whitey ):P

I'm an Ubuntu newbie too, having only dabbled a bit. I've also ended up with a download I'm not sure about, so I'm reading around, and stumbled upon your thread.

Just a couple of thoughts. Is everything fine with your HDDs? Have you done chkdsk, defrag, that kind of thing?
Have you tried running Ubuntu in Live mode? the option where no changes are made to your PC? Does it work on any of the machines you have access to?
My other thought was to buy a copy of Ubuntu. I got Feisty and Hardy from ebay. Cheap and quick (then you'll know it's not your dl that's the problem)

You've probably tried most of this, but I wanted to try and help, as I know how you feel :)

Good luck

Hello Annigma!

Thank you for your help. Im thinking that alot of people will be having the same problem as i am having right now, so i hope that when this problem is resolved other people may find this very useful for them as well...  If it helps people to use Linux as an OS, i cant see whats wrong with that.

But back to business, I have access to 2 laptops and a desktop computer. The laptop is 2 months old and has not been used much at all so far, the other laptop is a year old and the desktop (which has 2 hard drives) is a year old as well. The defrag has been done recently on the laptop and desktop , not on the other laptop though as it is new. 

Regarding the live mode, yes i have tried it many times on many copies on all the computers on different cds, different isos, and even on the usb drive. 

Very confusing!

The option of buying ubuntu is looking more and more like the answer to me, as i think i am unable to solve this.

I really dont want to quit trying to get Ubuntu working on my computer, but i have to say i have thought about it.

Someone must know the answer to this problem surely?

---

### Post by Bartender on 2009-11-12
whitey -
Do you have a friend with a fairly new, fast PC?  I've lost track of how many times you've tried downloading, but copy the download you feel best about to a thumb drive, take it to someone else's house, and try burning the CD on their PC.
Use good quality 700MB CD-R's, not generic crap.

---

### Post by whitey_1 on 2009-11-12
> **Bartender said:**
> whitey -
Do you have a friend with a fairly new, fast PC?  I've lost track of how many times you've tried downloading, but copy the download you feel best about to a thumb drive, take it to someone else's house, and try burning the CD on their PC.
Use good quality 700MB CD-R's, not generic crap.

Thanks Bartender,

I am going to buy some new writable cds today, and i will try it on my friends laptop, although mine are a good spec, i will give it a go.

Fingers crossed this time

---

### Post by kio_http on 2009-11-12
Redownload. If you're using windows use FDM (google it) If your on linux Downloadthemall or kget

---

### Post by marcopolo1981 on 2009-11-12
@Whitey_1
If you are going to go and buy new discs, may I recommend you buy re-writable discs?
It will save you money in the long run, and any half decent brands will allow you to re-uese them up to (and sometimes beyond in my experience) 10 times.
Also, when choosing them, ask one of the staff on that particular brand lowest burning speed.
The problem that you seem to have encountered is that some will only allow you to burn at 10x and upwards - no matter what software you are trying to burn the disk with. This is ok for music, but to host an operating system - it has to be extremely accurate. Choose a brand that allows very low burn speeds. Spending a couple of extra £'s on them is well worth it.

---

### Post by whitey_1 on 2009-11-12
Hi  Kio, Soapytheclown and members of the forum.


Thank you for the suggestions.

I went and bought new different branded cd-r's today. I got back and burned the iso to one of the new discs using imgburn, yet again though it would not burn it at 4x speed, it did burn it at 12x instead, and yet again the result was that there was a reported error with one of the files on the disc. 

I decided to try a dvd-rw, it did burn it at 4x speed, but i tried again to test the disc with ubuntu, and as before it reported an error with 1 file.

The current iso file i have been trying to use was fine with the hash check (confirmed earlier by members of this forum) However i did download and try to burn a new iso file, the same file as i tried before, but this time i got it from a torrent. The torrent file was the one listed on the ubuntu website. I burned it successfully to a dvd-rw at 4x speed, but again, after i tested the disc , it reported there was an error with 1 file.

The only thing i can think of trying next is to use a cd-rw disc, because i think this might be the only way to burn it at 4x speed.

Am i right in thinking this is all down to the fact i need to burn it at 4x speed on a cd-r disc? Am i also right in believing the original iso file i have downloaded is ok?

Im trying to eliminate all the possible reasons why this installation isnt working for me each time.

Thank you all for your help and patience,  any suggestions or comments are welcome as always.


Thank you

---

### Post by durand on 2009-11-12
It isn't this difficult to burn a cd...there must surely be a problem with your laptop's compatibility with ubuntu.

---

### Post by whitey_1 on 2009-11-12
> **durand said:**
> It isn't this difficult to burn a cd...there must surely be a problem with your laptop's compatibility with ubuntu.

I have burned the cds on 2 different laptop, one of which is only 2 months old. I find it unlikely that its a problem due to my hardware, because i have 3 computers.

---

### Post by durand on 2009-11-12
Sorry, I phrased that badly. What I meant was that I don't think its a problem with the way you're burning the cd but rather with the hardware itself which I don't think is fully compatible with ubuntu and therefore, ubuntu doesn't boot properly. You could try installing it via the alternative install. You may have a lot more luck there.

---

### Post by whitey_1 on 2009-11-12
> **durand said:**
> Sorry, I phrased that badly. What I meant was that I don't think its a problem with the way you're burning the cd but rather with the hardware itself which I don't think is fully compatible with ubuntu and therefore, ubuntu doesn't boot properly. You could try installing it via the alternative install. You may have a lot more luck there.


Hi Durand, 

That is a very interesting suggestion, i have yet to try the alternative version.

Could you tell me how to find the alternative version of the iso for ubuntu 9.10 , i have been looking at this page;
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I dont actually see it on there, i could be missing something, but i can only see Ubuntu 9.10 or Ubuntu 8.04 LTS versions. I only have 32bit architecture on all computers.

I cant see any other versions for me to download of Ubuntu 9.10.

Please could someone provide me with a link for the alternative version? Am i ok to burn the iso at 10x speed on a cd-r disc?

Thank you Durand and members of the forum.

---

### Post by durand on 2009-11-12
Here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

You needed to click on the Alternative Options link and then text based installer.

---

### Post by whitey_1 on 2009-11-12
> **durand said:**
> Here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

You needed to click on the Alternative Options link and then text based installer.


Thanks Durand!

I was looking and looking and just could not find that page, but im in the process of downloading it now. I hope it works with a cdr at 10x speed.

Time will tell, i will post back when (or if) i get this problem resolved.

Thanks again

---

### Post by whitey_1 on 2009-11-12
I must also add, if any of the members of the forum have any other suggestions, please add to this thread.

As always, all the help has been much appreciated

Thank you

---

### Post by Torinaz on 2009-11-12
> **whitey_1 said:**
> I must also add, if any of the members of the forum have any other suggestions, please add to this thread.

As always, all the help has been much appreciated

Thank you

Here is my two bits for your 32bit system.... hehehe,  when I first made the move from windows to Linux I only found one distro that would work with my system, that being Fedora, I could install it in under an hour, have it see and use all my hardware and run smoothly, but I liked the look of Ubuntu and the community support better, So eventually after many many hours of frustration with downloading and burning and what not of iso's and not having any luck with anything but Fedora, I finally went to the local Barns and Noble and bought a mag that came with the install disc for Ubuntu and have had no problems sense.  Good Luck

---

### Post by Bartender on 2009-11-12
I don't understand why you keep getting an error in one file.  You've tried most of the things that should isolate the problem - different burners, different downloads, etc. and you keep coming back with one error.

Weird.

Don't use CD-RW's.  Bad idea.  I've read dozens of posts on this forum from experienced operators over the last few years - CD-RW's cause problems.  

I've also read on this forum that sometimes the "Check Disc for Errors" utility reports errors when there aren't any.  Do you have a spare HDD you could slip into the PC and try installing even though it says there's an error?

---

### Post by whitey_1 on 2009-11-13
Hello everyone,

I have had a partial success! I downloaded and burned the alternative Ubuntu 9.10 onto a cdr and it reported no errors, i tested it to run it on my laptop without installing it, and it all run well!

However, i want this program for my desktop computer, so i tested on that computer. The disc check reported no errors, but it would not install or run without installing. It would appear to be loading, then after 2 minutes or so, the screen goes black and gradually the pc comes to a stop. I did leave it for a longer period, just to make sure this wasnt part of the set up stage, but when i returned to the pc the screen was black and nothing had installed.

So i am getting closer, i have a good copy of Ubuntu 9.10 on a cd now, but my desktop computer will not run it. 

I did try the usb installation way, but that was not successful at all. The computer gradually stopped and went to a black screen, without installing anything.

Would WUBI be a possibility to try next?

Please give me your suggestions.

Thank you

---

### Post by durand on 2009-11-13
WUBI isn't an option when using the alternative cd, I don't think.

---

### Post by whitey_1 on 2009-11-13
> **durand said:**
> WUBI isn't an option when using the alternative cd, I don't think.

That might rule out Wubi as a possibility then. Unless anyone else would like to comment on that point?

---

### Post by Iksf on 2009-11-13
Cant believe im about to say this  /cringe

Try installing openSUSE too check your hardware, Novell have excelent hardware relations. But delete it afterwoulds! xD

---

### Post by Dennis N on 2009-11-13
> **whitey_1 said:**
> ...The disc check reported no errors, but it would not install or run without installing. It would appear to be loading, then after 2 minutes or so, the screen goes black and gradually the pc comes to a stop. I did leave it for a longer period, just to make sure this wasnt part of the set up stage, but when i returned to the pc the screen was black and nothing had installed.
...


Didn't notice this being suggested so far in your thread (or I could have missed it), but have you tried adding the boot options:

```
acpi=off noapic nolapic
```

Press F6 on live CD (Other Options) at the first screen and add the above to the boot options line that appears. I suppose your alternate CD would have a similar option. It might help. 

This worked for me in the past to get Ubuntu installed on an old desktop which showed similar behavior.

Good luck.

---

### Post by annie227 on 2009-11-13
Whitey,I'm sorry to read of all the troubles you are having.
I recently came to Ubuntu and I love it.It is brilliant,a learning curve too but if I can do it anyone can.
I suggest you order the FREE cd
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
I did and haven't looked back (8.10) and now on reflection I realise I'm still learning but a convert nonetheless,and btw,burning my own iso's now of 9.10-if you knew me you'd be impressed because I have only recently owned a computer.Hang in there,it's worth it,soon you'll be flying and it's not only OPEN SOURCE,free,but highly creative,runs better,everything's better!My life is better!!!

---

### Post by whitey_1 on 2009-11-14
HI everyone,

Thanks again for your responses, i am aware of how long this is taking, but i am making real progress now as i have recieved 2 working versions of Ubuntu 9.10 (desktop and alternative versions). I checked both the discs and both of the report that no errors were found after the Ubuntu check facility.

However they still will not install.

I think i know what i have to do now to make them install, and i need advice on how to do this. 

When i start my computer without a Ubuntu disc in the cd-dvd drive am asked whether to start the machine with Windows or Ubuntu, obviously the Ubuntu option doesnt work. I think it is there due to a partial and failed previous attempt of mine to install the Ubuntu OS.

My question therefore is, how do i deinstall this partial installation of Ubuntu so i can reinstall it properly next time?

I have tried to find Ubuntu or Wubi on the add/remove programs facility, but neither appear on the list. I have formatted the second harddrive where i want the Ubuntu installed. 

Please can someone help advise me how to fully deinstall Ubuntu from my system? 

Thank you for all your help.

---

### Post by marcopolo1981 on 2009-11-14
Technically, you should be able to install over the Ubuntu installation that is already there. But because you are having difficulty in this respect, do the following:
 
**_I advise you to have your original XP Recovery Disc before you continue, otherwise you may be left with a PC that you can't install Ubuntu on, or boot back into XP either! If you are running Vista or Windows 7, I don't know how to do this as the instructions are different. You will need to google. I take no responsibility for you not making sure that these instructions are relevant to your *specific* needs!_**

#   From within windows, right click on "MY Computer" and select "Manage".

#   On the left side of the window, select "Disk Management".

#   On the right side of the window, right click on the partition that holds the current Ubuntu install and select "Delete Partition".

Restart your PC to check that XP still boots. If it does, you needn't go any further. If it doesn't, do the following:

#   Restart your PC with the XP Recovery Disc inserted.

#   When the setup asks you if you want to install or repair the current Windows install, press "R" to repair.

#   Enter the number that corresponds to the partition you wish to repair (Probably number 1).

#   Enter the Admin password for that PC 

#   You will get to a command prompt starting with
 C:WINDOWS>

#   Type: 
FIXMBR 

#   When prompted, press "Y" to confirm you are sure that you want to rewrite the Master Boot Record to make XP bootable again.

#   When it says that it has completed, type "exit" and remove the XP setup disc to prevent it from loading the setup again.

#   Reboot the PC.

You should now be back at booting XP without seeing any grub, and Ubuntu should now be completely removed from your system. If that didn't work, retrace the steps, and substitute "FIXMBR" for "fixboot x:" , where "x" is the drive XP is installed on. (ie. C:)
[B][U]
Again, I stress that these instructions are for people dual booting XP, **NOT** any other versions of Windows! I do not use Vista and I am not familiar with the recovery console that it provides. Google is your friend!;)[/U][/B] Microsoft give instructions for Vista at [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once you have successfully booted back into XP, and confirmed that Ubuntu is no longer on your system, try to boot your PC from the Ubuntu Live CD. Post back to either confirm or deny that you successfully booted into Ubuntu without installing, and we will try and take it from there.

---

### Post by rosswmcgee on 2009-11-14
I have open suse 11.2 it installed fine. I have 9.10 it installed fine. Same  type cd two identical computers, I can not install ubuntu on the suse computer, it stalls live it stalls install, made new cd same thing. I am perpelexed and not exactly new at this. I wanted to go 100% 9.10 but after 3 hours I am still sitting here stalled.

---

### Post by Bartender on 2009-11-14
whitey, I've lost track now of what is going on.

You say you have two HDD's?  

If so, the first one, with XP on it, will be identified as sda (or hda, same thing) by the Linux installer or a partitioner like GParted. 
And you have a second HDD, which is now devoid of data, where you want to install Ubuntu?  If so, the second drive will show up as sdb.
And when you turn the computer on, you come to a black-and-white screen?  Does it list Ubuntu kernel something-or-another, Ubuntu recovery, memtest, then it'll have a separator and it'll say Windows XP or Vista Longhorn?

Something like that?  I'm just trying to figure out what's happened and what you've got left.  It sounds to me like you *should* be able to install Ubuntu to sdb, and let GRUB auto-install (actually re-install if it's already there) to the Windows MBR.

Just to check, what happens if you choose Ubuntu?  Do you get a GRUB error?  What's the error?

What happens if you choose Windows?  Does Windows come up like it should?

---

### Post by whitey_1 on 2009-11-14
> **marcopolo1981 said:**
> Technically, you should be able to install over the Ubuntu installation that is already there. But because you are having difficulty in this respect, do the following:
 
**_I advise you to have your original XP Recovery Disc before you continue, otherwise you may be left with a PC that you can't install Ubuntu on, or boot back into XP either! If you are running Vista or Windows 7, I don't know how to do this as the instructions are different. You will need to google. I take no responsibility for you not making sure that these instructions are relevant to your *specific* needs!_**

#   From within windows, right click on "MY Computer" and select "Manage".

#   On the left side of the window, select "Disk Management".

#   On the right side of the window, right click on the partition that holds the current Ubuntu install and select "Delete Partition".

Restart your PC to check that XP still boots. If it does, you needn't go any further. If it doesn't, do the following:

#   Restart your PC with the XP Recovery Disc inserted.

#   When the setup asks you if you want to install or repair the current Windows install, press "R" to repair.

#   Enter the number that corresponds to the partition you wish to repair (Probably number 1).

#   Enter the Admin password for that PC 

#   You will get to a command prompt starting with
 C:WINDOWS>

#   Type: 
FIXMBR 

#   When prompted, press "Y" to confirm you are sure that you want to rewrite the Master Boot Record to make XP bootable again.

#   When it says that it has completed, type "exit" and remove the XP setup disc to prevent it from loading the setup again.

#   Reboot the PC.

You should now be back at booting XP without seeing any grub, and Ubuntu should now be completely removed from your system. If that didn't work, retrace the steps, and substitute "FIXMBR" for "fixboot x:" , where "x" is the drive XP is installed on. (ie. C:)
[B][U]
Again, I stress that these instructions are for people dual booting XP, **NOT** any other versions of Windows! I do not use Vista and I am not familiar with the recovery console that it provides. Google is your friend!;)[/U][/B] Microsoft give instructions for Vista at [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once you have successfully booted back into XP, and confirmed that Ubuntu is no longer on your system, try to boot your PC from the Ubuntu Live CD. Post back to either confirm or deny that you successfully booted into Ubuntu without installing, and we will try and take it from there.

I looked at the disc management, but i couldnt see another partition to delete. I will try a few other things first and then come back to your instructions if those do not work. 

Thanks for the instructions, i can see its something that is very important to get right as well.

---

### Post by whitey_1 on 2009-11-14
> **annie227 said:**
> Whitey,I'm sorry to read of all the troubles you are having.
I recently came to Ubuntu and I love it.It is brilliant,a learning curve too but if I can do it anyone can.
I suggest you order the FREE cd
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
I did and haven't looked back (8.10) and now on reflection I realise I'm still learning but a convert nonetheless,and btw,burning my own iso's now of 9.10-if you knew me you'd be impressed because I have only recently owned a computer.Hang in there,it's worth it,soon you'll be flying and it's not only OPEN SOURCE,free,but highly creative,runs better,everything's better!My life is better!!!

Hello Annie, 

Thank you for your helpful reply, i have now got 2 working discs (the alternative and desktop versions of Ubuntu 9.10)

It certainly is a step in the right direction!

I will keep going until i have resolved this problem because i have noticed how many interesting and beneficial points Ubuntu has. 

I cant wait to get it working! Thank you

---

### Post by whitey_1 on 2009-11-14
> **Bartender said:**
> whitey, I've lost track now of what is going on.

You say you have two HDD's?  

If so, the first one, with XP on it, will be identified as sda (or hda, same thing) by the Linux installer or a partitioner like GParted. 
And you have a second HDD, which is now devoid of data, where you want to install Ubuntu?  If so, the second drive will show up as sdb.
And when you turn the computer on, you come to a black-and-white screen?  Does it list Ubuntu kernel something-or-another, Ubuntu recovery, memtest, then it'll have a separator and it'll say Windows XP or Vista Longhorn?

Something like that?  I'm just trying to figure out what's happened and what you've got left.  It sounds to me like you *should* be able to install Ubuntu to sdb, and let GRUB auto-install (actually re-install if it's already there) to the Windows MBR.

Just to check, what happens if you choose Ubuntu?  Do you get a GRUB error?  What's the error?

What happens if you choose Windows?  Does Windows come up like it should?

Hello Bartender!

Thanks for the reply, i am sorry i have not been making myself clear enough, its been a new and very confusing process for me - to say the least!

My computer has 2 HDs , The primary one is a SATA drive with XP installed. The secondary one is an IDE HD which is blank, this is the one i would like to install Ubuntu on to.

When i start up my computer some white text on a black screen flashes up and maybe scrolls abit (i cant see what it says, it passes very quickly). After a few seconds i am presented with a menu with XP Windows or Ubuntu as possible selections.

If i choose XP Windows, the machine start as normal. If i select Ubuntu i arrive at black screen with this white writing:

[B]gnu grub version 1.97~beta4

[ minimal bash-like line editing is supported. For the first word, TAB lists possible command completions - anywhere else TAB lists possible device/file completions]

sh:grub>[/B]

This makes no sense to me, but this is what i am presented with when i select Ubuntu at start up. 

Does this make any sense?

Thank you

---

### Post by Cl0ud9 on 2009-11-14
> **whitey_1 said:**
> Hello Bartender!

Thanks for the reply, i am sorry i have not been making myself clear enough, its been a new and very confusing process for me - to say the least!

My computer has 2 HDs , The primary one is a SATA drive with XP installed. The secondary one is an IDE HD which is blank, this is the one i would like to install Ubuntu on to.

When i start up my computer some white text on a black screen flashes up and maybe scrolls abit (i cant see what it says, it passes very quickly). After a few seconds i am presented with a menu with XP Windows or Ubuntu as possible selections.

If i choose XP Windows, the machine start as normal. If i select Ubuntu i arrive at black screen with this white writing:

[B]gnu grub version 1.97~beta4

[ minimal bash-like line editing is supported. For the first word, TAB lists possible command completions - anywhere else TAB lists possible device/file completions]

sh:grub>[/B]

This makes no sense to me, but this is what i am presented with when i select Ubuntu at start up. 

Does this make any sense?

Thank you

If you want to install or re-install Ubuntu you have to boot from the cd. Correct me if I'm wrong, but it sounds like you are booting from your hard disk. You have to set bios to boot from the cd.

---

### Post by SuaSwe on 2009-11-15
Whoa, what an adventure, ey!

Out of curiosity, did you try your friend's burner in the end, or did you stick with only your own? If so, it's surely gotta be the burner (hardware) that's the problem. 

Secondly, is there any particular reason you're installing Karmic (9.10) as opposed to one of the older versions? This version seems to have some issues with ATI and Nvidia graphics drivers (I have for instance been unsuccessful in installing it on my machine, upon which 9.04 runs like a dream) - you may find that an older version installs without issue.

I wouldn't worry too much about the 'grub>' prompt as I'm guessing the intention is to overwrite the previous install and any traces of its bootloader anyway. :)

---

### Post by marcopolo1981 on 2009-11-15
@ Whitey_1
Firstly, please double check that you are in fact booting from the cd and not the second hard-disk, as ClOud9 posted.

The partition I said to delete is likely to be on the second hard-disk. But as you stated that it is blank in one of your recent posts, you can skip these steps. Just start from booting from your XP recovery disc, and follow from there.
This will restore your Master Boot Record as if you had never tried to install Ubuntu.
Once you can start from a clean slate, we will try and guide you from there.

Just a quick question, what is the exact make and model of the PC you are trying to install Ubuntu on? There may be some hardware incompatabilities that we can try to illiminate using Google.

---

### Post by whitey_1 on 2009-11-15
> **Cl0ud9 said:**
> If you want to install or re-install Ubuntu you have to boot from the cd. Correct me if I'm wrong, but it sounds like you are booting from your hard disk. You have to set bios to boot from the cd.

Hi Cloud,

I did try to reinstall the Ubuntu using the cd but that process failed. The BIOS is set to boot from the CD-dvd drive as primary, secondary is the SATA hd.

Thanks for the suggestion

---

### Post by whitey_1 on 2009-11-15
> **SuaSwe said:**
> Whoa, what an adventure, ey!

Out of curiosity, did you try your friend's burner in the end, or did you stick with only your own? If so, it's surely gotta be the burner (hardware) that's the problem. 

Secondly, is there any particular reason you're installing Karmic (9.10) as opposed to one of the older versions? This version seems to have some issues with ATI and Nvidia graphics drivers (I have for instance been unsuccessful in installing it on my machine, upon which 9.04 runs like a dream) - you may find that an older version installs without issue.

I wouldn't worry too much about the 'grub>' prompt as I'm guessing the intention is to overwrite the previous install and any traces of its bootloader anyway. :)

Hello SuaSwe,

My friend who burned the 2 cds on his computer sent them through the post for me, as he doesnt live close to me at all. 

Im only install version 9.10 because it is the latest version. That is an interesting point about the Nvidia issues because i have Nvidia graphics in this computer. Im not sure if that is the reason it wont install at such an early stage? The monitor goes black with a messege 'out of range' in the middle of the screen. That messege is coming from the monitor though, not directly from the computer i believe. So maybe it isnt compatible with my graphics card? i dont know, need suggestions on this one.

Regarding the GRUB prompt: you are right, i do just want to overwrite the previous installation (or partial installation, what ever it is i am let with right now) and any traces of the bootloader.

Yes it had been quite a process, i will definatly be posting a final reply when it comes as to what solved this problem. 

Thanks for you reply, and to everyone else who has helped.

---

### Post by whitey_1 on 2009-11-15
> **marcopolo1981 said:**
> @ Whitey_1
Firstly, please double check that you are in fact booting from the cd and not the second hard-disk, as ClOud9 posted.

The partition I said to delete is likely to be on the second hard-disk. But as you stated that it is blank in one of your recent posts, you can skip these steps. Just start from booting from your XP recovery disc, and follow from there.
This will restore your Master Boot Record as if you had never tried to install Ubuntu.
Once you can start from a clean slate, we will try and guide you from there.

Just a quick question, what is the exact make and model of the PC you are trying to install Ubuntu on? There may be some hardware incompatabilities that we can try to illiminate using Google.

Hello Marcopolo,

I have just checked my boot bios order it is as follows;

1: HL-DT-ST GCE-8527B  (LD cd-rw drive)
2: Hitachi HDP725032GL (Primary HD SATA 2)
3: IC35L120AVV207-0 (Secondary HD IDE)

They are set how the need to be as i understand. The IDE hd is blank, the Sata hd has everything on, Windows XP etc.

Now to find the recovery disc. Are they usually on a cd? i have never used one before, is it the only possible way of proceeding? 

My bought my motherboard earlier this year, it is a: GeForce 7050-MM. I didnt install it thats for sure!

I shall try and find my xp recovery disc. Would it be the disc with a certificate on the packet?

Thank you

---

### Post by marcopolo1981 on 2009-11-15
> **whitey_1 said:**
> Hello Marcopolo,

I have just checked my boot bios order it is as follows;

1: HL-DT-ST GCE-8527B  (LD cd-rw drive)
2: Hitachi HDP725032GL (Primary HD SATA 2)
3: IC35L120AVV207-0 (Secondary HD IDE)

They are set how the need to be as i understand. The IDE hd is blank, the Sata hd has everything on, Windows XP etc.

Now to find the recovery disc. Are they usually on a cd? i have never used one before, is it the only possible way of proceeding? 

My bought my motherboard earlier this year, it is a: GeForce 7050-MM. I didnt install it thats for sure!

I shall try and find my xp recovery disc. Would it be the disc with a certificate on the packet?

Thank you

Your Bios settings are correct.
The XP recovery disc is usually with the certificate on the packet.

As you are finding installing Ubuntu so difficult on that PC, I would think that restoring the MBR is the only logical next step.
I think we should postpone this and try something else first. If you can't find the XP recovery disc, don't worry, there are ways and means in obtaining one. PM me if you need advice in this respect.

Normally, Operating Systems can just be installed over the previous. I can't understand what is going wrong, as the discs you burned are free of defect, and the PC is set to boot from the disc drive first. There really shouldn't be anything stopping you from booting into a Live CD environment, even if you don't install it.

Before we go any further, Please go to [http://distrowatch.com/?newsid=05720](http://distrowatch.com/?newsid=05720) and download the pup-431.iso and burn it to a cd. It is a relatively small download, and works with just about any type of system. Burn it to a cd and try to boot from that. If you succeed in booting into the live environment, there should absolutely no reason that you shouldn't be able to do the same with Ubuntu. If you can't boot into Puppy, then we can assume it is something to do with your PC.
Please post back with your results.



Mark

PS. I applaud your persistence in trying to use Ubuntu. Most people, including myself if I am truly honest, would have said stuff it! and found another distro.=D>

---

### Post by whitey_1 on 2009-11-15
> **marcopolo1981 said:**
> Your Bios settings are correct.
The XP recovery disc is usually with the certificate on the packet.

As you are finding installing Ubuntu so difficult on that PC, I would think that restoring the MBR is the only logical next step.
I think we should postpone this and try something else first. If you can't find the XP recovery disc, don't worry, there are ways and means in obtaining one. PM me if you need advice in this respect.

Normally, Operating Systems can just be installed over the previous. I can't understand what is going wrong, as the discs you burned are free of defect, and the PC is set to boot from the disc drive first. There really shouldn't be anything stopping you from booting into a Live CD environment, even if you don't install it.

Before we go any further, Please go to [http://distrowatch.com/?newsid=05720](http://distrowatch.com/?newsid=05720) and download the pup-431.iso and burn it to a cd. It is a relatively small download, and works with just about any type of system. Burn it to a cd and try to boot from that. If you succeed in booting into the live environment, there should absolutely no reason that you shouldn't be able to do the same with Ubuntu. If you can't boot into Puppy, then we can assume it is something to do with your PC.
Please post back with your results.



Mark

PS. I applaud your persistence in trying to use Ubuntu. Most people, including myself if I am truly honest, would have said stuff it! and found another distro.=D>


Hello Mark,

Thanks for the instructions, i am in the process of downloading the pup-431.iso from the link you provided. I will post back as soon as i can to let you know how i got on. I have found the disc now, thanks for the offer of a pm i appreciate it alot.

Thanks also for the ps, i hope that this will be resolved at some point! it has been a long process, also a learning experience for me.

---

### Post by whitey_1 on 2009-11-15
Hello Mark (marcopolo) and members of the forum,

I downloaded the puppy iso and burned it to disc, rebooted the pc and it works. I am relieved that this version works, so at least my pc can work with a linux system. 

I will follow your instructions and use my Windows XP disc to try and fix my MBR.

I will post back soon as i have hopefully completed this step.

---

### Post by Bartender on 2009-11-15
whitey -
Let me guess.  Are you using an LCD monitor?  I've run into the exact same problem with the monitor reporting "Out of Range" when Ubuntu installer had to default to 640X480 during the install.  

This problem went away for me, and likely would for you too, if you can find a plain old CRT monitor to plug in.  LCD's want to run at their native resolution, CRT's don't care.  As a matter of fact, I'm keeping two old CRT's exactly because of this problem with new installations.

This is not going to be true every time, but very often if you can just get the OS installed, then get on the Internet, you can go to System>Hardware Drivers> and ask Ubuntu to look for any hardware drivers.  Chances are good that it will recognize your graphics card and go get the right drivers for it.

So I'm not saying this WILL solve your problem, but there's a good chance that a CRT will keep sending you a signal instead of saying "Out of Range" and you can install Ubuntu to that second HDD (sdb).  What you described back in post 63 tells me that GRUB is installed.  The error message you got when you tried to go to Ubuntu is not what I was expecting, but you probably have the new GRUB 2 installed.

I'm not saying DON'T do what others are suggesting, such as marcopolo's advice, but I think that you're actually very close to getting Ubuntu on that second drive if you can rustle up a CRT.

If you're already using a CRT, well, never mind...

---

### Post by whitey_1 on 2009-11-15
> **marcopolo1981 said:**
> Your Bios settings are correct.
The XP recovery disc is usually with the certificate on the packet.

As you are finding installing Ubuntu so difficult on that PC, I would think that restoring the MBR is the only logical next step.
I think we should postpone this and try something else first. If you can't find the XP recovery disc, don't worry, there are ways and means in obtaining one. PM me if you need advice in this respect.

Normally, Operating Systems can just be installed over the previous. I can't understand what is going wrong, as the discs you burned are free of defect, and the PC is set to boot from the disc drive first. There really shouldn't be anything stopping you from booting into a Live CD environment, even if you don't install it.

Before we go any further, Please go to [http://distrowatch.com/?newsid=05720](http://distrowatch.com/?newsid=05720) and download the pup-431.iso and burn it to a cd. It is a relatively small download, and works with just about any type of system. Burn it to a cd and try to boot from that. If you succeed in booting into the live environment, there should absolutely no reason that you shouldn't be able to do the same with Ubuntu. If you can't boot into Puppy, then we can assume it is something to do with your PC.
Please post back with your results.



Mark

PS. I applaud your persistence in trying to use Ubuntu. Most people, including myself if I am truly honest, would have said stuff it! and found another distro.=D>


Hello Mark, Bartender and members of the forum,

The puppy test completed successfully, i just run it without actually installing it.

I just tried to fix the MBR by rebooting with the Windows XP recovery disc, i chose the following options;

R (repair).
1 (selected the primary (and only) HD with Windows XP on).
Entered my password.
At the C prompt i entered 'fixmbr'

It did flash up a warning regarding a possible loss of data, but i went ahead anyway. It then seemed to do something very quickly, and asked me to reboot the system, which i did. When the system rebooted, i was still presented with the choice of booting Windows XP or Ubuntu.

I dont think it has worked, could i be wrong? did i do the right thing?

Thank you

---

### Post by whitey_1 on 2009-11-15
> **Bartender said:**
> whitey -
Let me guess.  Are you using an LCD monitor?  I've run into the exact same problem with the monitor reporting "Out of Range" when Ubuntu installer had to default to 640X480 during the install.  

This problem went away for me, and likely would for you too, if you can find a plain old CRT monitor to plug in.  LCD's want to run at their native resolution, CRT's don't care.  As a matter of fact, I'm keeping two old CRT's exactly because of this problem with new installations.

This is not going to be true every time, but very often if you can just get the OS installed, then get on the Internet, you can go to System>Hardware Drivers> and ask Ubuntu to look for any hardware drivers.  Chances are good that it will recognize your graphics card and go get the right drivers for it.

So I'm not saying this WILL solve your problem, but there's a good chance that a CRT will keep sending you a signal instead of saying "Out of Range" and you can install Ubuntu to that second HDD (sdb).  What you described back in post 63 tells me that GRUB is installed.  The error message you got when you tried to go to Ubuntu is not what I was expecting, but you probably have the new GRUB 2 installed.

I'm not saying DON'T do what others are suggesting, such as marcopolo's advice, but I think that you're actually very close to getting Ubuntu on that second drive if you can rustle up a CRT.

If you're already using a CRT, well, never mind...

Hello Bartender,

I just looked up my monitor on google, this is the exact model;
BenQ FP91G+ - 19" TFT active matrix LCD display

I would be very interested to know what happens if i plug in an old style monitor, i think i might have one in the loft somewhere, i shall try that and let you know how i get on. Its interesting to think there might be something going on without the monitor actually being able to pick it up.

These are all good suggestions, thank you all for being so helpful, this really is a great forum!

---

### Post by Bartender on 2009-11-15
Yeah, like I said, LCD's are touchy about resolution.  They want their native resolution.  They'll display resolutions other than native, but you'll see ghosting and fuzziness.  Once you get too far from native resolution (like the 640X480 that the ubuntu installer defaults to when it can't figure out what to do with the graphics card) the LCD gives up and posts that error message.

If you'd fixed the mbr, the PC would boot straight to Windows.

Plugging in an old CRT and tossing either one of your Ubuntu discs in the tray might be easier than struggling with fixmbr at this point.  

Way I see it, there's no point in fixing the mbr because WIndows will boot and reinstalling Ubuntu to the second drive will rewrite the MBR with GRUB anyway.  But that's just my 2 cents...

IF you plug in a CRT, and IF you can install Ubuntu, and IF you can then get online and get the correct drivers for your graphics card, turn the PC off, plug your LCD back in, and reboot.  You should get a picture, and then you should be able to set the correct resolution if it doesn't go to it automagically

---

### Post by Linux&amp;Gsus on 2009-11-15
I just stumbled upon this thread but didn't read it all, too long. Sorry if this is redundant or irrelevant for you.

I had once the problem that I wanted to install Kubuntu (9.04) on someones desktop. But for the love of it, I couldn't, the computer froze no matter if LiveCD or Alternate. And yes, I used those same CDs before and I used them later on with no problem.
Then, just out of curiosity, I tried Ubuntu and and it worked just fine on the first go.

So, it might be worth a try to check another Ubuntu version. As in Kubuntu or Xubuntu. You'll never know if that works unless you tried it.
Also, it is possible to install, say, Xubuntu and if you would prefer it to then install the Gnome desktop after successful installation of Xubuntu.

In any case, I hope it'll work out for you in the end and you'll get what you want.


Cheers,
L&G

---

### Post by marcopolo1981 on 2009-11-15
> **Bartender said:**
> 
Way I see it, there's no point in fixing the mbr because WIndows will boot and reinstalling Ubuntu to the second drive will rewrite the MBR with GRUB anyway.  But that's just my 2 cents...


This is correct. Typically, reinstalling any OS will rewrite the MBR. But as Whitey_1 asked how to completely uninstall Ubuntu in post #57, I offerred advice. Also, starting from scratch can also help to trouble shoot each step along the way.
If trying an older monitor helps, way to go! 

If it doesn't and you still wish to completely remove Ubuntu from your system, run the XP recovery cd again, 
#   press R
#   enter your password
#   press 1, then type:
   fixboot C: 

Because you can boot Puppy, it is quite safe to say that your PC is Linux compatible - it just might need some tweaking to fix resolution, etc...

---

### Post by whitey_1 on 2009-11-15
Hello members of the forum,

Since i tried the old monitor, i have been able to install the Ubuntu. So it had been a success, almost.

After i installed Ubuntu, i was prompted to remove the disc and restart the computer. When the system started i was presented with the GRUB menu with 3 options. Start Windows XP, Ubuntu or Ubuntu recovery mode (i think thats what it said). I selected Ubuntu and came to a black screen with white text asking for me to login with an Ubuntu login and Password.

I cant remember assigning a Login or Password though.

I remember it asking me to assign a hostname before, which pressed enter to select the default 'Ubuntu' hostname.

I am stuck with this screen now, i have tried a few Logins and Passwords, but it is not working, and i dont know what they could be.

Please help, i am nearly there with this problem now.

Thank you

---

### Post by halitech on 2009-11-15
the info here should help

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Bartender on 2009-11-15
Or just reinstall Ubuntu again!

On the third, (or is it fourth?) step of installation, before the partitioning step, it's going to ask you for your name, a user name, and a password.
You don't remember that part??

Anyway, you could just reinstall, and when you get to that page, WRITE DOWN what you enter.  You'll notice that as you type your name, the "username" will automatically fill in.  Don't let that throw you.  You can mouse down to the username, delete the auto-filled field, and put in whatever you want.  My advice: make it simple.

Then type in a password, twice, and my advice here is to make it simple again, unless you really do have security concerns.  Mine is only four letters.  Ubuntu will pop up with a message saying the password is not complex enuf, but you can click OK or Ignore or whatever it is and move past the message.  
If you tick "Auto log-in" on the bottom of the page Ubuntu will just come up without asking for username/password.  

But you still need to know that password because any time you want to do anything administrative (like getting updates) you have to enter it!

EDIT: I just went and visited aysiu's link, the one halitech posted.  That's pretty cool.  Probably a little faster than re-installing!!

---

### Post by whitey_1 on 2009-11-15
> **halitech said:**
> the info here should help

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Hi Halitech, 

Thanks for that link, i have had a look and it looks very useful. There is a problem though, i cant remember any username either. I do remember assigning a hostname as 'Ubuntu'

Does anyone know what the login would be if i went with the default?

Im sorry to have to ask this, its just got so confusing the last few days!

Thank you everyone.

---

### Post by halitech on 2009-11-15
once you get to the root shell, if you do
```
ls /home
```
it will list your username then do 
```
passwd *username*
```
then type in the password and confirm it
change *username* to what shows up when you do ls /home
then exit and reboot

---

### Post by whitey_1 on 2009-11-15
> **halitech said:**
> once you get to the root shell, if you do
```
ls /home
```it will list your username then do 
```
passwd *username*
```then type in the password and confirm it
change *username* to what shows up when you do ls /home
then exit and reboot

Thanks Haliltech,

How do i get to the root shell? i have it at [B]ubuntu login:

[/B]Am i at the wrong screen?


If i start it in Ubuntu recovery mode, i eventually get to this prompt;
**root@ubuntu:~#**

I tried typing in 
ls /home

But nothing happens, i just go back to the **root@ubuntu:~# **prompt.

How do i get to the root shell?


I am very close now, just need to log in correctly!

---

### Post by halitech on 2009-11-15
you are at the root prompt. The # indicates you are in the root account.

if ls /home gives no output then somehow you bypassed the user account setup part of the install. Not sure how you would do that but it seems like you did. You did type it as LS /HOME (in all lowercase) and not 1s (the number 1 s)

I'm not sure if there is anyway of adding a user and setting it up properly to be the primary user or not. You may have to resort to reinstalling again.

---

### Post by whitey_1 on 2009-11-15
> **halitech said:**
> you are at the root prompt. The # indicates you are in the root account.

if ls /home gives no output then somehow you bypassed the user account setup part of the install. Not sure how you would do that but it seems like you did. You did type it as LS /HOME (in all lowercase) and not 1s (the number 1 s)

I'm not sure if there is anyway of adding a user and setting it up properly to be the primary user or not. You may have to resort to reinstalling again.

Hi Halitech,

I certainly did type that in all lowercase, many times. It just presents me with the same prompt every time. 

It does certainly look like i have to reinstall Ubuntu then. Do i put the alternative Ubuntu disc in? because that was the one i used to install it.

I have just rebooted with the disc in the drive. The menu that appears has the following options;

[B]Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disc[/B]
[B]Rescue a broken system
[/B]
I can only think that i need to choose** install Ubuntu **?

---

### Post by halitech on 2009-11-15
Maybe try the repair broken system first and see if that does any good. If not, then do the install ubuntu option.

---

### Post by whitey_1 on 2009-11-15
Hi Everyone,

I have been trying to reinstall the Ubuntu system, but for some reason, things are not going to plan. Im exactly sure what i did, so i would like to do a full installation from scratch?.

Would it be possible for me to just login in to windows and format my second hard drive again, to start a full installation again from fresh?

It is only the second hard drive, and it was empty before anyway. It is the hard drive where i want to install Ubuntu.

do you think that would be ok for me to proceed this way?


Thank you

---

### Post by Cl0ud9 on 2009-11-15
> **whitey_1 said:**
> Hi Everyone,

I have been trying to reinstall the Ubuntu system, but for some reason, things are not going to plan. Im exactly sure what i did, so i would like to do a full installation from scratch?.

Would it be possible for me to just login in to windows and format my second hard drive again, to start a full installation again from fresh?

It is only the second hard drive, and it was empty before anyway. It is the hard drive where i want to install Ubuntu.

do you think that would be ok for me to proceed this way?


Thank you

Sure it would be OK, but there is no need to take the time and log into windows and format the drive that way. You can reinstall Ubuntu over your first installation and Ubuntu should format the drive for you.

---

### Post by marcopolo1981 on 2009-11-16
Because you only see a black screen with white writing, I am assuming the install process flawed. You seem to not have the GUI installed, or at least it doesn't start. Also, if you don't remember setting up a username or password, it is possible that this step was skipped somehow.. These are very important steps.
It makes sense to reinstall ubuntu. 
As ClOud9 said, there isn't any point in deleting the partition from within windows, as you now know that you CAN install Ubuntu. Those steps That I gave were to make sure that you wasn't left with an unbootable system, should your PC not allow you to install Ubuntu.

---

### Post by Bartender on 2009-11-16
+1
Just reinstall right over the existing install.  I've done that plenty of times w/out any trouble.

Like I said, when you get to that page that asks for your name, a user name, and a password, write down whatever you type in.

Let's say you decide to go with something really simple.  On one of my test boxes I use "suby" for username and "nut" for password, so I'll use that as an example.

As far as I can tell, when you get to that step in the installation where it wants these entries, it doesn't really matter if you type in your full name.  So you could just type in "suby" in the first window, and suby will auto-fill in the username window.

Then mouse down to password and type in "nut".  I think you have to enter it twice, don't you?  Sheesh, I just did an install last week and I don't remember.  Anyway, type it in, hit Enter, you get the box that says the password is too weak, tell it OK or Confirm (I don't remember what that is exactly either) and click the "Log me in automatically" radio button on the bottom of the page.

Then "Forward" on to the next part of the installation.

Reinstallation would be good practice anyway!

EDIT:  I forgot to mention that if and when we finally get you going, and you've downloaded installed the Nvidia hardware drivers, turn off the PC, plug your LCD monitor back in, and turn the monitor on *before* you start the PC.  I'm not sure that will help with monitor detection, but I think it will.  Once you've got Ubuntu working with the Nvidia drivers and your LCD monitor, you won't have to start the monitor first.

---

### Post by The Cog on 2009-11-16
Installing over an existing installation requires using the custom partitioning option and knowing what you are doing. It may be easier to use the live CD, go into System->Administration->gparted
and use that partition editor to find and delete the ext4 partition. You can leave the linux swap partition there and DON'T delete any FAT or NTFS partitions! After this, you can just use the installer option to install into the largest unused space, which of course will be where the ext4 partition was.

Beware that as soon as you delete the ext4 partition, the GRUB bootloader won't be able to boot the machine (it needs files that were on that partition), so you will need to complete the reinstall of Linux before you can even boot windows again.

If the problems you are having are all to do with monitor out of range, then the text-mode alternate installer should still work for you. The questions are the same - it's just the presentation that's slightly different. You need to remember to use tab, space and enter to be able to navigate the menus - sometimes it's not obvious exactly where the "focus" is until you hit tab.

---

### Post by whitey_1 on 2009-11-16
Hi everybody,

Thanks again for all your replies and help.

I have just installed Ubuntu again, from fresh on my second HD. I assigned a username and password, which i have made sure i made a note of this time.

I got to the part where it instructed me to remove the disc and select continue to reboot the computer. The computer started up, loaded GRUB, i selected Ubuntu. After a few seconds the screen went from the black screen with white writing to a sort of scrambled mix of green ish lines and other colours. 

The screen does not display anything recognizable at all. To restart the computer i found that i can press ctrl+alt+del and then press enter. So i think the Ubuntu has installed, its just that my monitor does not display it correctly. This was using the old style monitor. The newer monitor (TFT one) just displays a messege 'out of range'.

I dont have any access to any other monitors.

So i am stuck with this, i hope someone has a suggestion about what i can do from here.

Thank you


EDIT: I have just tried the CTRL+ALT+DEL then ENTER again to restart, and that doesnt work. So please ignore that part of this messege.

---

### Post by halitech on 2009-11-16
can you press CTRL + ALT + F1 and get the terminal window? If you can, log inusing the username and pasword you set up and then we will need to configure your video card.

---

### Post by whitey_1 on 2009-11-16
I just thought of something, i dont know if it is relevant.

I have just installed Ubuntu using the alternative version, should i try installing it again with the desktop version?

---

### Post by halitech on 2009-11-16
no, both versions end up with the same installed version

---

### Post by whitey_1 on 2009-11-16
> **halitech said:**
> can you press CTRL + ALT + F1 and get the terminal window? If you can, log inusing the username and pasword you set up and then we will need to configure your video card.

Hi Halitech,

I cant see any GUI, ive only ever seen the sort of basic screens, the ones like you see when you first boot the computer.

Sorry, i got confused, it wasnt ctrl alt del, but i can shut down the computer with keys, im doing it blind because the screen is scrambled.

I wish i was that far into it though!


EDIT:

Sorry that didnt make any sense. What i was meaning to say was that i think the Ubuntu has loaded up but i just cant see it. It does seem to respond to keys being pressed, because by trial and error i have managed to shut the system down. I just cant see anything of what i am doing.

---

### Post by halitech on 2009-11-16
If its a graphics issue (which I think it is) then pressing CTRL+ALT+F1 will give you the terminal which should work properly.

---

### Post by whitey_1 on 2009-11-16
> **halitech said:**
> If its a graphics issue (which I think it is) then pressing CTRL+ALT+F1 will give you the terminal which should work properly.

Hi Halitech,

I just tried that. I pressed ctrl+alt+f1 and it took me to a black screen with white text. I entered my username and password. Now i am at a prompt saying
whitey@ubuntu:~$

Please can you tell me where i go from here?

---

### Post by Bartender on 2009-11-16
What's the exact graphics device?  What does Windows say it is?  IIRC you said it was nVidia but not the exact one.

Reason I ask is you might find it easier to just pop a newer nVidia card in.  I've had good luck with the ASUS EN8400GS.

EDIT:  While we're waiting for halitech, I googled around some.  Take a look at this from Ubuntu Docs:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I'm going to suggest one or two cautious steps.  Monkeying around with the terminal can be scary.

Maybe print out the first part of this.  See where it talks about dynamically setting differnt resolutions?  It's the second section, almost at the top of the article.  Try going back to the terminal line like halitech said and type in 

xrandr

after the dollar sign and hit the Enter key.

You should get an output similar to the one in the guide.  I just tried xrandr on my laptop and got a message much like the one described.  See that line that says "screen 0:" then it has a minimum, current, and maximum?  Write down the min/current/max, then close the terminal, and post back here.  We keep talking about this, someone who has some experience with this is bound to pipe up!

Sorry you're having so much trouble but I think we're close enuf that all we need is someone who's worked thru this to say what's needed..

Oh, I almost forgot - what is your LCD monitor's native resolution and refresh rate?  Should be easy to find by googling or looking thru the paperwork...

---

### Post by whitey_1 on 2009-11-16
> **Bartender said:**
> What's the exact graphics device?  What does Windows say it is?  IIRC you said it was nVidia but not the exact one.

I have the box here that the motherboard came in. The computer doesnt have a separate graphics card, it is built in. The details are as follows;

GeForce 7050M-M motherboard
Nvidia GeForce 7050 PV
Nvidea purevideo

Are those the details needed? Or shall i reboot with windows and look under system maybe?

---

### Post by Bartender on 2009-11-16
No, that helps a lot.  Take a look at this bug report in launchpad

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425372](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425372)

Looks like the 7050PV is a bugger in 9.10.  Don't know about 9.04.

Post #7 might help you.  I was never sure about whether you can install restricted drivers via LiveCD but this guy says that's what he did.

Post #9 indicates another way to go about it but I expect it won't make sense to a Linux newbie.

So you just happen to be one of those lucky folks who has a troublesome Nvidia chipset.  Post #7 looks like the best bet to me.

EDIT:  Sheesh - just google "ubuntu 7050PV".  Lots of hits.

[http://www.td-e.com/tip/ubuntu-with-nvidia-Geforce-7050-PV.php](http://www.td-e.com/tip/ubuntu-with-nvidia-Geforce-7050-PV.php)

Here's an old one from the nvforums...

[http://www.nvnews.net/vbulletin/showthread.php?t=127365](http://www.nvnews.net/vbulletin/showthread.php?t=127365)

No way someone who's new to Linux could follow that, though.

If you've got a few bucks laying around, and a PCI-X slot on that motherboard, a basic Ubuntu-compatible nVidia card might be the easiest solution...

---

### Post by halitech on 2009-11-16
ok, so we know the system is installed and we are looking at graphics issues.
run this
```
lspci | grep VGA
```

also, lets see if we are connected by pinging [www.google.com](www.google.com) and see if we get a positive result.

If you are connected, run
```
sudo apt-get update && sudo apt-get upgrade
```
you will need to enter your password, just type it in and don't worry that nothing shows up.

if you are using 32bit Ubuntu, run this
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run
```
if its 64bit, run
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run
```
Then follow the instructions here: [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

---

### Post by Bartender on 2009-11-16
halitech -
Thanks for coming back, man.

I was in over my head...:)

EDIT:  whitey, that funny symbol between "lspci" and "grep" is usually on the key just below the "Backspace" key.  That's where it is on my Dell keyboard anyway.  It's an upper-case symbol and is often shown on the key as two little vertical dashes, one right above the other.  The lower case symbol on that same key is \.

I don't think you'll be able to do it, but if you could bring this thread up on the Ubuntu PC you could copy/paste halitech's commands directly into the terminal.  If you can't you'll have to do it by hand.  It would be more reliable to copy/paste, that way we'd know the command was entered exactly as halitech wrote it.  But since you can't get a display up...

---

### Post by whitey_1 on 2009-11-16
> **halitech said:**
> ok, so we know the system is installed and we are looking at graphics issues.
run this
```
lspci | grep VGA
```also, lets see if we are connected by pinging [www.google.com]("http://www.google.com") and see if we get a positive result.

If you are connected, run
```
sudo apt-get update && sudo apt-get upgrade
```you will need to enter your password, just type it in and don't worry that nothing shows up.

if you are using 32bit Ubuntu, run this
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run
```if its 64bit, run
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run
```Then follow the instructions here: [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)




Hi Halitech and Bartender,

Thanks very much for both of your replies, brilliant stuff.

I have been looking at that link you sent to me Halitech, i am about to follow those steps, but i am abit concerned about this part of the instructions;


      ' It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR=Red]THIS IS MANDATORY![/COLOR]_** '

I dont understand about uninstalling previous version, i have only done the standard installation with the alternative Ubuntu 9.10 disc. Would this mean i have a version already? do i have a current drive to disable? Im not sure how to complete this part of the process, please can you advise me here?

---

### Post by halitech on 2009-11-16
they are referring to any other Nvidia versions that you may have installed. If you have a fresh install and haven't enabled anything you are fine to go ahead.

---

### Post by whitey_1 on 2009-11-16
> **Bartender said:**
> No, that helps a lot.  Take a look at this bug report in launchpad

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425372](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/425372)

Looks like the 7050PV is a bugger in 9.10.  Don't know about 9.04.

Post #7 might help you.  I was never sure about whether you can install restricted drivers via LiveCD but this guy says that's what he did.

Post #9 indicates another way to go about it but I expect it won't make sense to a Linux newbie.

So you just happen to be one of those lucky folks who has a troublesome Nvidia chipset.  Post #7 looks like the best bet to me.

EDIT:  Sheesh - just google "ubuntu 7050PV".  Lots of hits.

[http://www.td-e.com/tip/ubuntu-with-nvidia-Geforce-7050-PV.php](http://www.td-e.com/tip/ubuntu-with-nvidia-Geforce-7050-PV.php)

Here's an old one from the nvforums...

[http://www.nvnews.net/vbulletin/showthread.php?t=127365](http://www.nvnews.net/vbulletin/showthread.php?t=127365)

No way someone who's new to Linux could follow that, though.

If you've got a few bucks laying around, and a PCI-X slot on that motherboard, a basic Ubuntu-compatible nVidia card might be the easiest solution...

I think you could be right, if nothing else works from now on Bartender, i will seriously consider buying a graphics card to put in there.

---

### Post by whitey_1 on 2009-11-16
> **Bartender said:**
> halitech -
Thanks for coming back, man.

I was in over my head...:)

EDIT:  whitey, that funny symbol between "lspci" and "grep" is usually on the key just below the "Backspace" key.  That's where it is on my Dell keyboard anyway.  It's an upper-case symbol and is often shown on the key as two little vertical dashes, one right above the other.  The lower case symbol on that same key is \.

I don't think you'll be able to do it, but if you could bring this thread up on the Ubuntu PC you could copy/paste halitech's commands directly into the terminal.  If you can't you'll have to do it by hand.  It would be more reliable to copy/paste, that way we'd know the command was entered exactly as halitech wrote it.  But since you can't get a display up...


Hi Bartender,

Good point there about that code, i will take extra care making sure i write it out 100% correct. 
I found the '|' key on this laptop on the same key as the \ key as you say. I hold shift and press '\' to get the '|'.

Is there 2 versions of the '|' key?

---

### Post by whitey_1 on 2009-11-16
> **halitech said:**
> they are referring to any other Nvidia versions that you may have installed. If you have a fresh install and haven't enabled anything you are fine to go ahead.


Thanks for clearing that point up Halitech. I will be starting the process shortly, i will post back soon as i can to let you know how i got on.

---

### Post by halitech on 2009-11-16
should only be 1 of them, placement may be different on laptops compared to desktops but it is usually Shift + \

---

### Post by whitey_1 on 2009-11-16
> **Bartender said:**
> halitech -
Thanks for coming back, man.

I was in over my head...:)

EDIT:  whitey, that funny symbol between "lspci" and "grep" is usually on the key just below the "Backspace" key.  That's where it is on my Dell keyboard anyway.  It's an upper-case symbol and is often shown on the key as two little vertical dashes, one right above the other.  The lower case symbol on that same key is \.

I don't think you'll be able to do it, but if you could bring this thread up on the Ubuntu PC you could copy/paste halitech's commands directly into the terminal.  If you can't you'll have to do it by hand.  It would be more reliable to copy/paste, that way we'd know the command was entered exactly as halitech wrote it.  But since you can't get a display up...

Hi Bartender and members of the forum,

On the black screen with white writing, when i press shift+\ it comes up as the ¦ symbol instead of the | symbol 

Is it definatly ok to use what appears to be the ¦ symbol is this instance?

thanks

---

### Post by halitech on 2009-11-16
If that is what you have on your system then try it, worse that will happen is you will get a message saying invalid command.

---

### Post by whitey_1 on 2009-11-16
> **halitech said:**
> ok, so we know the system is installed and we are looking at graphics issues.
run this
```
lspci | grep VGA
```also, lets see if we are connected by pinging [www.google.com]("http://www.google.com") and see if we get a positive result.

If you are connected, run
```
sudo apt-get update && sudo apt-get upgrade
```you will need to enter your password, just type it in and don't worry that nothing shows up.

if you are using 32bit Ubuntu, run this
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run
```if its 64bit, run
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run
```Then follow the instructions here: [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

Hi Halitech,

Thanks for those instructions.  I followed them until the part where i have to ping google. At the prompt i typed this;

**ping [www.google.com](www.google.com)**

I dont think it worked because it came back with this;

**ping: unknown host [www.google.com](www.google.com)**


I then entered 

**sudo apt-get update && sudo apt-get upgrade**

I was then prompted for my password, which i entered. It is a very simple 4 character long password, all lowercase as well. The computer came up with this;

[B]Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security release.gpg
      Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
      Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
       Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB[/B] 

The last part of that was at the bottom of the screen, i could not scroll down at all, so i dont know if the messeges continued down the screen further. Also i was left with no prompt to write to after that, so i had no choice but to ctrl+alt+del and restart the computer.

I dont know if this is relevant, but as i have installed Ubuntu on my second harddrive, i dont see how the internet connection will work as all the internet connections etc were set up on the primary hard drive.

Where do you suggest i should go from here?

Thank you for all your help!

---

### Post by itsbrad212 on 2009-11-16
K3B never gives me a bad burn :D

---

### Post by halitech on 2009-11-16
> **whitey_1 said:**
> Hi Halitech,

Thanks for those instructions.  I followed them until the part where i have to ping google. At the prompt i typed this;

**ping [www.google.com](www.google.com)**

I dont think it worked because it came back with this;

**ping: unknown host [www.google.com](www.google.com)**


I then entered 

**sudo apt-get update && sudo apt-get upgrade**

I was then prompted for my password, which i entered. It is a very simple 4 character long password, all lowercase as well. The computer came up with this;

[B]Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security release.gpg
      Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
      Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
       Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB[/B] 

The last part of that was at the bottom of the screen, i could not scroll down at all, so i dont know if the messeges continued down the screen further. Also i was left with no prompt to write to after that, so i had no choice but to ctrl+alt+del and restart the computer.

I dont know if this is relevant, but as i have installed Ubuntu on my second harddrive, i dont see how the internet connection will work as all the internet connections etc were set up on the primary hard drive.

Where do you suggest i should go from here?

Thank you for all your help!

ok, so you aren't connected in Ubuntu for some reason. What type of connection do you have? ie, dialup, dsl, cable, satellite?

still in the terminal, run
```
lspci | grep Ethernet
```and then post the info here

the fact that windows is installed on the primary drive doesn't matter, connection shouldn't be only available to the primary drive

---

### Post by The Cog on 2009-11-17
For some reason your internet isn't working. You're really having a bad time of it, aren't you.

Plug the ethernet cable in before rebooting. After booting, use the command: **ifconfig eth0**
You should see a line that includes BROADCAST RUNNING. If you don't see RUNNING then the ethernet isn't working. Then you're really in trouble. Assuming it is, then DHCP should also give you an IP address and you should see a line starting with **inet addr:**.

Other folks:
Is there any reason you're advising downloading the nvidia drivers from nvidia rather than the Ubuntu repositories? I would have suggested these two commands myself:
[b]sudo apt-get update
sudo apt-get install nvidia-glx-185 nvidia-settings[/b]

---

### Post by whitey_1 on 2009-11-17
> **halitech said:**
> ok, so you aren't connected in Ubuntu for some reason. What type of connection do you have? ie, dialup, dsl, cable, satellite?

still in the terminal, run
```
lspci | grep Ethernet
```and then post the info here

the fact that windows is installed on the primary drive doesn't matter, connection shouldn't be only available to the primary drive

Thanks Halitech, i will be doing this tonight and posting back with the results. Ive been held up getting home and back on the computer. 

Thanks again for your reply, i will be replying again soon as possible.

---

### Post by Annigma on 2009-11-17
Wow, you're like a dog with a bone whitey! Good on you! 
I hope you get it sorted soon. You certainly deserve to!
:)

---

### Post by Kai69 on 2009-11-17
Try using one of these burners i used the xp version i made 5 disks no problems useing 2year old disks burn iso at slowest speedx4 hope this helps.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by whitey_1 on 2009-11-17
> **halitech said:**
> ok, so you aren't connected in Ubuntu for some reason. What type of connection do you have? ie, dialup, dsl, cable, satellite?

still in the terminal, run
```
lspci | grep Ethernet
```and then post the info here

the fact that windows is installed on the primary drive doesn't matter, connection shouldn't be only available to the primary drive

Hi Halitech,

I ran the code you said in the terminal and got this response;

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

Thank you

---

### Post by whitey_1 on 2009-11-17
> **The Cog said:**
> For some reason your internet isn't working. You're really having a bad time of it, aren't you.

Plug the ethernet cable in before rebooting. After booting, use the command: **ifconfig eth0**
You should see a line that includes BROADCAST RUNNING. If you don't see RUNNING then the ethernet isn't working. Then you're really in trouble. Assuming it is, then DHCP should also give you an IP address and you should see a line starting with **inet addr:**.

Other folks:
Is there any reason you're advising downloading the nvidia drivers from nvidia rather than the Ubuntu repositories? I would have suggested these two commands myself:
[B]sudo apt-get update
sudo apt-get install nvidia-glx-185 nvidia-settings[/B]

Hello the Cog

I run the code you gave me (ifconfig eth0) and it responded with;

[B]eth0
Link encap:Ethernet  HWaddr 00.21.97.97.9b.55
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/B]

Im not sure if that is a good response or not.

Please let me know what you think.

Thank you.

---

### Post by whitey_1 on 2009-11-17
> **halitech said:**
> ok, so you aren't connected in Ubuntu for some reason. What type of connection do you have? ie, dialup, dsl, cable, satellite?

still in the terminal, run
```
lspci | grep Ethernet
```and then post the info here

the fact that windows is installed on the primary drive doesn't matter, connection shouldn't be only available to the primary drive

I am not sure what type of connection i have. I have a router box with a small aerial on it. It is a wireless system, i know for sure it isnt dialup. If there is any other details that i could find to help, please let me know.

Thank you for all your help, it is much appreciated i can assure you.

---

### Post by whitey_1 on 2009-11-17
> **Annigma said:**
> Wow, you're like a dog with a bone whitey! Good on you! 
I hope you get it sorted soon. You certainly deserve to!
:)

Hi Annigma,

Thanks for the response, it certainly has been a long process - and it would appear that i am not out of the woods yet!

I appeciate you sending me the email. Im very impressed with this forum and the members, they have been very helpful with this long problem.

Ill keep going though.

Thanks for your messege.

---

### Post by halitech on 2009-11-17
ok, so you are using wireless
[color="red"]01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)[/color]

what is the output of ```
sudo ifconfig
```and
```
sudo iwlist scan
```

---

### Post by Bartender on 2009-11-17
whitey -
You don't know how you get your internet?
  
What feeds the router that has the antenna sticking out of it?  Is it cable, like a coaxial antenna cable, or is it a telephone line?  
Is this a combined modem/router?
Are there Ethernet ports on the back of the router?  If so, you should definitely try turning the PC off, plugging in a length of Ethernet cable to the router and to the PC, then turn the PC back on and boot into Ubuntu.  This would in all likelihood be less problematic than the Atheros wireless card.

Man, between the funky graphics chipset and the Atheros wireless, we've got ourselves an uphill battle...

Wwe're going to need to know what kind of internet service you've got, and it would probably be helpful to have the modem and the router models.  If it's a combined modem/router, give us that model #, OK?

Last time I checked Comcast cable internet would not work when hooked directly to a Linux PC.  Comcast wants to see a Windows PC at the other end of the line.  But once you get the service started using a Windows PC, Linux works just fine if you put a router between the Comcast modem and the Linux PC.  So we could bash our heads against the wall trying Linux fixes and the problem might be something else entirely.

---

### Post by whitey_1 on 2009-11-17
> **halitech said:**
> ok, so you are using wireless
[COLOR=red]01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)[/COLOR]

what is the output of ```
sudo ifconfig
```and
```
sudo iwlist scan
```

Hi Halitech,

The output of **sudo ifconfig** is:
[B]eth0
Link encap:Ethernet  HWaddr 00.21.97.97.9b.55
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns: carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:31 Base address:0x4000

lo
Link encap:Local Loopback[/B]

The output of **sudo iwlist scan** is:
[B]lo
Interface doesn't support scanning

eth0
Interface doesn't support scanning.

wmaster0
Interface doesn't support scanning.

wlan
Scan completed :
Cell 01 - Address: 00:16:E3:DD:41:0c
Channel:1[/B]



For some reason though, when i start typing in this black screen with white writing, it wont scroll! The computer seems to lock up once i get to the end of the screen. I have to ctrl+alt+del every time and restart. Is there something i can do about this?

Should i maybe buy a new graphics card? As this one i have has compatibility problems.

Thank you

---

### Post by halitech on 2009-11-17
ok, wlan0 is your wireless card and it looks like it is working and it found something but I'm guessing the ESSID is set to not broadcast. Do you have access to the router to check the settings?

have you ever been able to connect to this wireless router?

---

### Post by marcopolo1981 on 2009-11-18
@ Whitey
Is there any possiblity that you have an ethernet cable you could use/borrow from one of the other PC's?
These problems will be much easier to solve once you are connected to the internet.
Once you have garphics, then we can worry about your wireless - one problem at a time.

Setting up WiFi can be done easiest from the GUI, for new linux users

---

### Post by whitey_1 on 2009-11-20
Hi Everyone,

I have some good news - i have managed to install Ubuntu and it is working, but there are parts of it that are not working.

I bought and installed a graphics card to bypass the conflicting one that was built in on the motherboard. So i do have a GUI to work with now, i can imagine things will be abit easier now i can see what i am doing.

The problems are now though that i still cannot connect to the internet. Ubuntu is installed entirely on my secondary hard drive, nothing else is on that drive. It can see the secondary drive, i can view the files. My avg antivirus is not visible on there to me, i could be wrong about that. 

Should i be starting a new thread now as the exact question i asked in the title of this thread has been resolved, maybe?

If it is appropriate to do so, please let me know what you think about the problems i mentioned.

Thank you all so much for your help, you have been brilliant.

---

### Post by marcopolo1981 on 2009-11-21
> **whitey_1 said:**
> Hi Everyone,

I have some good news - i have managed to install Ubuntu and it is working, but there are parts of it that are not working.

I bought and installed a graphics card to bypass the conflicting one that was built in on the motherboard. So i do have a GUI to work with now, i can imagine things will be abit easier now i can see what i am doing.

The problems are now though that i still cannot connect to the internet. Ubuntu is installed entirely on my secondary hard drive, nothing else is on that drive. It can see the secondary drive, i can view the files. My avg antivirus is not visible on there to me, i could be wrong about that. 

Should i be starting a new thread now as the exact question i asked in the title of this thread has been resolved, maybe?

If it is appropriate to do so, please let me know what you think about the problems i mentioned.

Thank you all so much for your help, you have been brilliant.

Well done for your persistence!

All of the programs that you installed via XP will not work in Ubuntu, including AVG. There is not much call for anti-virus in any Linux Distro, as there are very few true Linux virii. For the programs you use in Windows, linux has free alternatives. ie. Microsoft Office ---> OpenOffice.org

Have you tried to use an ethernet cable to connect to your router? This should be as simple as plugging one end into the router and ther other into the back of your PC.
Once you are connected, update Ubuntu and you may find that it presents you with drivers to download - which will be the easiest resolution. If not, we will need to know more about the wireless card.

---

### Post by Bartender on 2009-11-21
> **marcopolo1981 said:**
> Well done for your persistence!

Have you tried to use an ethernet cable to connect to your router? This should be as simple as plugging one end into the router and ther other into the back of your PC.
Once you are connected, update Ubuntu and you may find that it presents you with drivers to download - which will be the easiest resolution. If not, we will need to know more about the wireless card.

+1

Still want to know what kind of internet service you have - cable, DSL, etc.

Sometimes just plugging in the Ethernet cable to the PC might not work.  You may have to physically unplug (not just turn off) the router for a few minutes so that it dumps its settings, turn it back on, then wait a few minutes for it to stabilize, then plug in the Ethernet cable to router and PC, then turn on the PC and try to boot into Linux.  Hard-wired internet usually "just works", wireless can be more complicated because of wireless chipset inside the PC and wireless encryption might be confusing to you until you've done it a few times in Linux.

Sorry to hear you had to go buy a graphics card, but glad you found a compatible one!  It's awful hard to make progress when you can't see anything on the screen ;)

EDIT:  Can you post the name and model of the graphics card you bought?  Always curious about aftermarket cards that work out of the box.

---

