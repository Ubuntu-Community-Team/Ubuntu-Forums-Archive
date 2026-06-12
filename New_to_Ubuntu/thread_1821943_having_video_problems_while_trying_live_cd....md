---
title: "having video problems while trying live cd..."
date: 2011-08-09
forum: New to Ubuntu
---

### Post by mjloesch99 on 2011-08-09
I was trying to get the latest version of ubuntu, and I downloaded it onto a flash drive and attempted to boot from the flash drive but when I clicked run live it said something about the moniter being on the wrong resolution. I read something about using the terminal to fix it but I'm not sure I can on my computer.

---

### Post by Redblade20XX on 2011-08-09
Can you post a screen shot of the error?

- Red

---

### Post by mjloesch99 on 2011-08-09
No, I've been forced to resort to my phone because the internet is so slow... the warning reads" PC video resolution setting is out of range change setting to recommended resolution 1280x1024 @60Hz" I tried going into my panel on windows xp and changing it that way, but no luck.

---

### Post by beew on 2011-08-09
'The latest version' is which one? 11.04 or 11.10? If it is 11.10 then it is an alpha and is expected to be broken in some way.

What is your graphic card?

---

### Post by kaldor on 2011-08-09
Can you tell us what graphics card you have?

---

### Post by mjloesch99 on 2011-08-09
Its a RADEON X3000 and it is ubuntu 11.04. There could be something very small im missing, considering im new to ubuntu.

---

### Post by mjloesch99 on 2011-08-10
Would this problem persist if i just installed it?

---

### Post by amjjawad on 2011-08-10
> **mjloesch99 said:**
> I was trying to get the latest version of ubuntu, and I downloaded it  onto a flash drive and attempted to boot from the flash drive but when I  clicked run live it said something about the moniter being on the wrong  resolution. I read something about using the terminal to fix it but I'm  not sure I can on my computer.

> **mjloesch99 said:**
> No, I've been forced to resort to my phone  because the internet is so slow... the warning reads" PC video  resolution setting is out of range change setting to recommended  resolution 1280x1024 @60Hz" I tried going into my panel on windows xp  and changing it that way, but no luck.


Are you running Ubuntu 11.04 from a [LiveCD ]("https://help.ubuntu.com/community/LiveCD")or [LiveUSB]("http://en.wikipedia.org/wiki/Live_USB")?

What XP has to do with Ubuntu?

---

### Post by mjloesch99 on 2011-08-10
Live usb

---

### Post by amjjawad on 2011-08-10
> **mjloesch99 said:**
> Would this problem persist if i just installed it?

I suggest not to install now unless everything will work just fine with you. That's the main idea behind The Live Session.

---

### Post by amjjawad on 2011-08-10
> **mjloesch99 said:**
> Live usb

[http://ubuntuforums.org/showthread.php?t=1251150](http://ubuntuforums.org/showthread.php?t=1251150)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mjloesch99 on 2011-08-10
> **amjjawad said:**
> I suggest not to install now unless everything will work just fine with you. That's the main idea behind The Live Session.

Any ideas on fixing this? I still dont fully understand what exactly isnt working

---

### Post by mjloesch99 on 2011-08-10
Ughhhh how do i get this thing working?

---

### Post by amjjawad on 2011-08-10
> **mjloesch99 said:**
> Any ideas on fixing this? I still dont fully understand what exactly isnt working

I did post some links for you. Have you checked these links or not yet? if you haven't yet, please do :)

---

### Post by snipe_photo on 2011-08-10
Hi I am having a similar problem.  I am attempting to install xubuntu using a livecd.  The cd boots and I can get to the splash screen on both the try without installing and the installer itself but after a few seconds I lose output.  I looked at the links but I am not sure what boot option to try.

---

### Post by mjloesch99 on 2011-08-10
> **mjloesch99 said:**
> Ughhhh how do i get this thing working?

> **amjjawad said:**
> I did post some links for you. Have you checked these links or not yet? if you haven't yet, please do :)

I did get the link, but I don't get that screen. I looked around for safemode but I couldn't find anything, I got a menu using f1 through 10 and they were boot options. However I think that these options were for problems after installation. For example I tried going into rescue mode but it needed something to rescue... How do I reach the option for safemode, with the current interface?

---

### Post by amjjawad on 2011-08-11
> **mjloesch99 said:**
> I did get the link, but I don't get that screen. I looked around for safemode but I couldn't find anything, I got a menu using f1 through 10 and they were boot options. However I think that these options were for problems after installation. For example I tried going into rescue mode but it needed something to rescue... How do I reach the option for safemode, with the current interface?

Do you get this screen when you boot your machine from your LiveUSB?

[IMG]http://techgage.com/articles/linux/ubuntu_1104_natty_narwhal_review/ubuntu_install_02_thumb.jpg[/IMG]

---

### Post by Wim Sturkenboom on 2011-08-11
Ubuntu in it's eternal wisdom has decided to hide that screen :(

When you boot from the live cd, you should get a screen with 2 small 'icons' at the bottom. One a keyboard, the other one a human in a circle. If you get that far, press <esc> and you will get the above shown menu. If you don't get that far, let us know.

---

### Post by Chopped on 2011-08-11
I have an idea..... don't flame me if I am wrong though. I just using Ubuntu about a week ago. My first LiveCD I made had an error in it, so it would not load properly when I went to install. I had to burn another disc and ran the Check disc for errors option to make sure, that worked for me.

---

### Post by amjjawad on 2011-08-11
> **Chopped said:**
> I have an idea..... don't flame me if I am wrong though. I just using Ubuntu about a week ago. My first LiveCD I made had an error in it, so it would not load properly when I went to install. I had to burn another disc and ran the Check disc for errors option to make sure, that worked for me.

After you download any iso for any distro, please make sure to check MD5SUM.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by amjjawad on 2011-08-11
> **Wim Sturkenboom said:**
> Ubuntu in it's eternal wisdom has decided to hide that screen :(

When you boot from the live cd, you should get a screen with 2 small 'icons' at the bottom. One a keyboard, the other one a human in a circle. If you get that far, press <esc> and you will get the above shown menu. If you don't get that far, let us know.

Just like GRUB menu, it's hidden if Ubuntu is the only OS installed on your system unless you press and hold Shift Key.
Same for booting from LiveCD or LiveUSB, if you don't press any key in few seconds, it will boot automatically and if I'm not wrong, it should give you the option to install or try on a GUI screen.

You right, a key has to be pressed to get that screen in the previous post :)

---

### Post by mjloesch99 on 2011-08-11
> **amjjawad said:**
> Do you get this screen when you boot your machine from your LiveUSB?

[IMG]http://techgage.com/articles/linux/ubuntu_1104_natty_narwhal_review/ubuntu_install_02_thumb.jpg[/IMG]

I have reached that page once. I believe i hit help then typed menu. However, when i try to do this again, I get the little person in a circle thing, and then it begins booting and gives me the error... whenever it starts booting I try to abort with esc but it usually goes 
rightt ahead

---

### Post by amjjawad on 2011-08-11
> **mjloesch99 said:**
> I have reached that page once. I believe i hit help then typed menu. However, when i try to do this again, I get the little person in a circle thing, and then it begins booting and gives me the error... whenever it starts booting I try to abort with esc but it usually goes 
rightt ahead

Whenever you see that little fellow, Press any key (space for example) and you'll get the language list. Choose your Language and then Press F6.

---

### Post by amjjawad on 2011-08-11
Have you checked MD5SUM before creating the LiveUSB/LiveCD?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If not, please do that because that supposed to be [your first step]("https://www.facebook.com/note.php?note_id=152426241466147").

What software/tool you used to create the LiveUSB?

---

### Post by Wim Sturkenboom on 2011-08-11
> **amjjawad said:**
> ... Same for booting from LiveCD or LiveUSB, if you don't press any key in few seconds, ...It would be oh so nice to have a simple text there so a user knows that pressing a key will achieve something. I know that this is not the place to complain about these things but this 'design' is simply braindead and the one that came up with this has less knowledge of user interfaces than a shrimp.

---

### Post by amjjawad on 2011-08-11
> **Wim Sturkenboom said:**
> It would be oh so nice to have a simple text there so a user knows that pressing a key will achieve something. I know that this is not the place to complain about these things but this 'design' is simply braindead and the one that came up with this has less knowledge of user interfaces than a shrimp.

Oh well, I wish the developers can read this!

Edit:
What is a MUST IMHO is: If you want to install GRUB to some other place like sda1 (which is for Windows) instead of sda, a warning message should pop up. I believe this will reduce LOTS of problems and threads here and above all, will save everyone's time. But again, what can I say?

---

### Post by mjloesch99 on 2011-08-11
> **amjjawad said:**
> Have you checked MD5SUM before creating the LiveUSB/LiveCD?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If not, please do that because that supposed to be [your first step]("https://www.facebook.com/note.php?note_id=152426241466147").

What software/tool you used to create the LiveUSB?

I just used the instructions on the ubuntu download page, not to sound like an idiot but i dont understammnd this hash checker thing...

---

### Post by amjjawad on 2011-08-11
> **mjloesch99 said:**
> I just used the instructions on the ubuntu download page, not to sound like an idiot but i dont understammnd this hash checker thing...

If you did read the link I posted and you didn't understand anything, then I'm not sure how can I explain it more clearly than it's already explained in that link.

What part you didn't understand?

MD5SUM: [http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
Ubuntu Community Documentation: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

When you download 700MB file from the internet, there is a chance that your downloaded file might be corrupted or damaged. In order to check the integrity of your downloaded file and make sure it's not broken, damaged or corrupted then you need to check the MD5SUM for it.

How to do that?


From Windows: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Windows

From Linux: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Linux

From Mac OS X: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Mac OS X

---

### Post by mjloesch99 on 2011-08-11
So, I did the hash check thing, and everything checked out. I can now get to that menu consistently by hitting any key as you said. When I looked on the one link under f4 there was a safe boot mode option but now its not there... I checked all of the options under f6, and that got me farther then usual, but I was immediately lost.

---

### Post by mjloesch99 on 2011-08-12
> **mjloesch99 said:**
> So, I did the hash check thing, and everything checked out. I can now get to that menu consistently by hitting any key as you said. When I looked on the one link under f4 there was a safe boot mode option but now its not there... I checked all of the options under f6, and that got me farther then usual, but I was immediately lost.

Scrathch that lost part.

---

