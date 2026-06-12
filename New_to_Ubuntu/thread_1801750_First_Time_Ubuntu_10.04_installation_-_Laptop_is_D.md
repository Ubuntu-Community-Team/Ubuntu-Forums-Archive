---
title: "First Time Ubuntu 10.04 installation - Laptop is Dying :'("
date: 2011-07-11
forum: New to Ubuntu
---

### Post by ajsoulmate on 2011-07-11
Hello everyone,

My Fiancée asked me to start this thread to help her to fix her problem.

She finally decided to give Ubuntu a try and if things will work out for her, she'll get rid of Vista (not sure how she can use that anyway) and install Ubuntu.

[B]She doesn't have a laptop now to write this so I'm doing it on her behalf.
[/B]

Her Laptop is HP Pavilion DV5 - Intel Due Core - 4GB RAM - 300GB HDD and I think it's 64-bit.

After downloading Ubuntu 10.04.2 from Ubuntu's Website, problems started to happen:

1- Her DVD/CD-Drive did not detect the blanks CDs she tried to insert to burn the Ubuntu image. She never used it but for some weird reason it did not work.

2- I told her she needs to create a LiveUSB instead. She got a 4GB USB and when she tried to create one, her laptop couldn't detect the new USB :(

3- She said that my laptop has started unexpectedly to shut down all by itself.

4- We tried to create a backup for the laptop but each and everytime we try to move files to an external HDD, Laptops goes OFF.

5- I thought it's because of Windows Vista (for some reason I thought that) so we tried to create the LiveUSB but we couldn't. The Laptop couldn't detect the new Flash Drive (4GB).

6- I asked her to do something else. I asked her to remove the RAMs (she got two, each is 2GB) and turn the laptop. Then insert one of them ONLY and turn the laptop on again.

THAT DID WORK. The transfer rate for the data from internal HDD to the external one was LESS THAN 1MB/sec.
Now, it's 15MB/sec.

7- I thought it's better to test the other RAM. I asked her to turn it off again, take the first RAM and insert the other one.

8- Once the 2nd RAM was inserted, the laptop could not ever login to Windows any more :(

IT IS ALWAYS STOPS at a black screen with blinking white dash (-) and that's all.

9- We tried to reset the BIOS to default settings. DID NOT HELP.

10- Funny thing is, when we tried to put the RAM which did work before, the laptop did not work as well and the blinking dash was always there.

11- Tried to but all the RAMs together but it did not help as well.

12- We did a RAM TEST from BIOS and it says that everything is ok. Test Pass. However, the laptop could not pass the blinking dash.

13- BIOS is detecting the RAM, both of them.

She's on the phone with me now and the same problem happened.

Now, what could be the reason and how we can save the files and install Ubuntu?

Is the laptop dead? 

It seems a Hardware issue more than a Software one but she feels bad because she wanted to try Ubuntu and now, she almost lost her laptop :(

Your help is much appreciated.

Thank you!

---

### Post by Bucky Ball on 2011-07-11
Sounds like something's not right hardware-wise but this is all occurring in Windows. You might have better luck on a Windows forum. ;)

Having said that, certainly sounds like a hardware issue and if not, a software issue, a Vista one, that is.

---

### Post by ajsoulmate on 2011-07-11
> **Bucky Ball said:**
> Sounds like something's not right hardware-wise but this is all occurring in Windows. You might have better luck on a Windows forum. ;)

Having said that, certainly sounds like a hardware issue and if not, a software issue, a Vista one, that is.

No, not really. We can NOT even login to Windows anymore

We just want to create the LiveUSB, boot the machine, save the files, format and install Ubuntu.

We are STUCK on that blinking dash with black screen and we can't do anything except entering BIOS.

I don't trust Windows Forum, I trust this community :)

---

### Post by Bucky Ball on 2011-07-11
Fair enough. Well, if you boot the machine and only have Windows on it and all you get is a blinking cursor, there is something wrong with Windows or your hardware is dying (although which bit is yet to be discovered). If you can't boot from the LiveCD, I'd say lean toward hardware death.

You are setting the BIOS to boot from the USB or CD/DVD, whichever you are using? Silly question, but ...

---

### Post by mastablasta on 2011-07-11
it could be that the motheboard is dying. shutting off by itself could mean bad capacitors on the motherboard. 
 
only blinking cursor is very strange. it's as if no device is connected at all to it. it would be best to take it to HP service unless you know how to handle notebooks yourself. 
 
also if you have a manual - there should be boot error codes there.usually errors are given out by beeps. i dont' know if this goes for notebooks as well. usually one short beep means all is ok on boot, more or different kind of beeps (for example long one) they mean something is wrong.
 
is the BIOS detecting hard disk? does it detect CD player?

---

### Post by ajsoulmate on 2011-07-11
> **Bucky Ball said:**
> Fair enough. Well, if you boot the machine and only have Windows on it and all you get is a blinking cursor, there is something wrong with Windows or your hardware is dying (although which bit is yet to be discovered). If you can't boot from the LiveCD, I'd say lean toward hardware death.

You are setting the BIOS to boot from the USB or CD/DVD, whichever you are using? Silly question, but ...

I thought it's Windows Issue but looks like it's a Hardware issue. I just don't get it. It worked super fast and prefect with one RAM Chip (2GB) but never did again.

Problem is, I can't create any live media :(
I'm far away from my girl and I'm trying to help her while I'm away.

I thought it was one of the RAM Chips but apparently, there is something else?!

---

### Post by ajsoulmate on 2011-07-11
> **mastablasta said:**
> it could be that the motheboard is dying. shutting off by itself could mean bad capacitors on the motherboard. 


As far as I know, if there is something wrong with the MB, then it should stop completely but perhaps I'm wrong.


> only blinking cursor is very strange. it's as if no device is connected at all to it. it would be best to take it to HP service unless you know how to handle notebooks yourself. 

It's for my fiancée and I'm trying to help her remotely :(
I think she has to do that eventually but I thought it's better to try few steps first. She wants to buy new one but I refused.

 
> usually one short beep means all is ok on boot, more or different kind of beeps (for example long one) they mean something is wrong.

Well, when the Blinking Cursor/Dash is there, and when I asked her to Press Esc, there was a BEEP. 2-3 seconds beep then 0.5 sec beeps. That's only when she hits ESC for few times.

>  
is the BIOS detecting hard disk? does it detect CD player?
That what will make me crazy. BIOS IS detecting everything O_o

---

### Post by mastablasta on 2011-07-11
> **ajsoulmate said:**
> As far as I know, if there is something wrong with the MB, then it should stop completely but perhaps I'm wrong.

 
No, it can also act up similary like yours.
 
 
 
> 
It's for my fiancée and I'm trying to help her remotely :(
I think she has to do that eventually but I thought it's better to try few steps first. She wants to buy new one but I refused.

It might be cheaper to fix it. doesn't seem to me like the maschine is that old.
 
 
> 
Well, when the Blinking Cursor/Dash is there, and when I asked her to Press Esc, there was a BEEP. 2-3 seconds beep then 0.5 sec beeps. That's only when she hits ESC for few times.

beeps should be automatic. not "key pressing beeps". 
 
> 
That what will make me crazy. BIOS IS detecting everything O_o
 
Ok it could be that the monitor is not detected or some other hardware issue, or that boot sector is missing (see google for repair Vista MBR). it could be boot sector is there but corrupt (pointing elsewhere).
 
that's why a factory repair is a good choice in this case. it's hard to diagnose remotely like this, while they have the tools and knowhow. notebooks often don't use some generic equipment like PC, so it could also be that some special HP driver got corrupt (maybe :-) ). anyway i am sure they will fix it to boot or tell you what hardware problem it is (if it is hardware issue).
 
edit - funny thing is that live CD or USB should be able to boot with no disk inside. normal troubelshooting procedure in your case would be to unplug all systems and then add one by one, trying to see which works and which doesn't. unless ofcourse motherbaord is dead...

---

### Post by Terl on 2011-07-11
Have you tried checking the bios to make sure it is set to try and boot from CD first?  If so, try your windows disk to see if it boots.  If it does you could try a repair of the vista installation (if your intent is to keep Vista).  If it does boot from a cd you could get someone else to provide an Ubuntu disk for her and boot from that.  If it boots you may be able to rescue any files from the Vista disk using the Ubuntu cd running live.

When the machine first starts does it generate any beeps as it starts?  If so write the pattern down; they are error beeps.

It is entirely possible it is hardware, but it would be good to try a bootable cd, like Ubuntu, or even your windows recovery disc to see what happens.

---

### Post by halibaitor on 2011-07-11
Sounds to me that you might have a problem with the RAM.  Try the following procedure:

Remove both RAM chips, and with a pencil eraser, gently scrub the edge connectors until they are a nice shiny gold color (both sides).
Then very carefully brush off all of the eraser crumbs and re-install the RAM.

Can't hurt to try.  Just be careful.  :D

---

### Post by ajsoulmate on 2011-07-11
> **mastablasta said:**
> No, it can also act up similary like yours.

It might be cheaper to fix it. doesn't seem to me like the maschine is that old.


I hope that's not true in our case. The machine is not that old indeed and we did not expect such issue and can't offered to buy new one. 
 

> beeps should be automatic. not "key pressing beeps". 
 
Got it.
If so, then there is NO BEEPS when we removed the RAM or when one of the chips was inserted.
 

> Ok it could be that the monitor is not detected or some other hardware issue, or that boot sector is missing (see google for repair Vista MBR). it could be boot sector is there but corrupt (pointing elsewhere).
My first diagnose was a Software Error but after what happened later, I'm afraid there is something else.
Another funny thing is, the laptop is NOT over heating.

 
> that's why a factory repair is a good choice in this case. it's hard to diagnose remotely like this, while they have the tools and knowhow. notebooks often don't use some generic equipment like PC, so it could also be that some special HP driver got corrupt (maybe :-) ). anyway i am sure they will fix it to boot or tell you what hardware problem it is (if it is hardware issue).
 
If she just had a backup for her files, we would have done a system recovery which already comes with the laptop and if that did not help, we can format.
Now, we just need to take the info out then we can do whatever we want.

> 
edit - funny thing is that live CD or USB should be able to boot with no disk inside. normal troubelshooting procedure in your case would be to unplug all systems and then add one by one, trying to see which works and which doesn't. unless ofcourse motherbaord is dead...


That's the thing. She needs another machine in order to create a LiveCD or LiveUSB. That laptop is the only machine she got and I'm too far from her. Hope she can find another machine with some friends or family. That's the only option rather than sending it to service and God knows what will they do ... they may format it and she'll lose all her stuff.

Actually, that's what we have done without the Live Media.
I asked her to take the RAMs, etc as explained above.
But yes, that was without a Live Media.

---

### Post by ajsoulmate on 2011-07-11
> **Terl said:**
> Have you tried checking the bios to make sure it is set to try and boot from CD first?  If so, try your windows disk to see if it boots.  If it does you could try a repair of the vista installation (if your intent is to keep Vista).  If it does boot from a cd you could get someone else to provide an Ubuntu disk for her and boot from that.  If it boots you may be able to rescue any files from the Vista disk using the Ubuntu cd running live.

When the machine first starts does it generate any beeps as it starts?  If so write the pattern down; they are error beeps.

It is entirely possible it is hardware, but it would be good to try a bootable cd, like Ubuntu, or even your windows recovery disc to see what happens.

I already answered these Qs in my previous posts :)

I'll ask her to create a LiveCD or USB on another machine and only then, we can try to rescue the files and format the stupid Vista. God, I hate Vista so much.

Again, NO BEEPS at all unless we press ESC. We removed RAM but nothing happened but light flashing. All the lights were flashing on the laptop, that's all.

I just don't get it ... it was working with one of the RAM but then it stopped completely.

---

### Post by MlDean on 2011-07-11
did you by any chance install a new stick of ram ?  ram will cause them to crash like that , when i buy ram i test it with Memtest 86+ , you can download the ISO and burn it to a cd put it in restart the PC and it should boot right up , if it kicks out any errors in a test , the ram is bad , i have had some video cards act like that too .

---

### Post by ajsoulmate on 2011-07-11
> **MlDean said:**
> did you by any chance install a new stick of ram ?  ram will cause them to crash like that , when i buy ram i test it with Memtest 86+ , you can download the ISO and burn it to a cd put it in restart the PC and it should boot right up , if it kicks out any errors in a test , the ram is bad , i have had some video cards act like that too .

No, NO NEW RAM were inserted at all.

RAM TEST in BIOS was fine. Every time we did the test, the result was PASS. However, not sure yet if that was a correct report. It's a tool/feature that comes with the BIOS.

---

### Post by FormatSeize on 2011-07-11
> **mastablasta said:**
> It could be that the motheboard is dying. shutting off by itself could mean bad capacitors on the motherboard. 
This is most likely the case. I've had this happen to me not too long ago, and I was experiencing a lot of the same issues. Actually, they were pretty much the exact same issues. First, the DVD drive stopped working, then the CD drive started failing, and one day, it simply refused to boot. I could boot from a USB, but then that stopped working as well.
 
When you cut on the computer, does it make an sort of beeping sound.

---

### Post by Cpierce on 2011-07-11
I echo running the mem86 test and not just the BIOS test to check ram. Also, start Ubuntu, and go to "disk utility" click on the hard drive to make sure it is healthy. I had a bad drive that would boot up fine and then crash at random.

---

### Post by MG&amp;TL on 2011-07-11
Just to echo halibaitor, do try cleaning everything (carefully) that looks like copper pins, flat pieces of copper, or cable-ends. The coppery bits are usually on the edge of pieces of PCB. Also check very carefully for loose wires, although I appreciate this is difficult on a laptop :(

It's just that I had something very similar to this on an (ancient, second hand) desktop pc. Eventually cleaned everything and found a dodgy connection on one of the internal cables. Seemed to work fine after that. Still working now. :D

---

### Post by ajsoulmate on 2011-07-11
> **FormatSeize said:**
> When you cut on the computer, does it make an sort of beeping sound.

Again, there is NO beep sound UNLESS ESC is pressed.

This is a Laptop not a PC.

---

### Post by ajsoulmate on 2011-07-11
> **Cpierce said:**
> I echo running the mem86 test and not just the BIOS test to check ram. Also, start Ubuntu, and go to "disk utility" click on the hard drive to make sure it is healthy. I had a bad drive that would boot up fine and then crash at random.

That would be super great if we do have a LiveCD or USB but fact is, we do NOT have any :(

Thanks anyway :)

---

### Post by ajsoulmate on 2011-07-11
> **MG&TL said:**
> Just to echo halibaitor, do try cleaning everything (carefully) that looks like copper pins, flat pieces of copper, or cable-ends. The coppery bits are usually on the edge of pieces of PCB. Also check very carefully for loose wires, although I appreciate this is difficult on a laptop :(

It's just that I had something very similar to this on an (ancient, second hand) desktop pc. Eventually cleaned everything and found a dodgy connection on one of the internal cables. Seemed to work fine after that. Still working now. :D

It's a Laptop that NO ONE uses except her.
She does not even use her CD/DVD drive and it stopped working for some weird reason.

She is at work now. Once she'll come back home, we'll try some other steps.

Problem is, I'm trying to help her while I'm very far away from her, not even in the same city.

Thanks anyway :)

---

### Post by ajsoulmate on 2011-07-11
Something is telling me it's a Hardware issue even though I keep my fingers crossed and wish it's a Software issue.

I'm afraid it's the Mother Board is failing or perhaps the RAM. Or, it could be the HDD?
Really confusing.

Steps that I'll ask my fiancée to do:

1- Try to create a LiveUSB (CD/DVD Drive might not work) from another machine. Not sure if she'll manage to do that or not? she got only one laptop and it's dying already.

2- Take the HDD out. At least, we need to make sure what's going on. If the HDD is out and there is no other media to boot from, there must be an error message on screen. If the same Blinking Dash will appear again, then it's not the HDD.

3- If step 1 and 2 fail, we have no other option but to send it to maintenance.



I just talked to her over the phone and she told me that she tried to do a Recovery to the system (HP Tools) this morning before leaving to work and it did NOT work :(


I know it's a bit complicated but I hope someone here knows what's going on. I appreciate all your support and help as always but I'm looking for someone who have faced the same issue and managed to fix it :)

THANK YOU ALL :D

---

### Post by FormatSeize on 2011-07-11
A bad hard drive shouldn't cause anything else to fail. Something I just thought of, though, try taking out or unplugging the optical drive. 
 
When my other computer failed, I kept parts of it like the HDD and optical drives. The CD drive from my old computer works well. But then I replaced it with an additional DVD drive, and my computer won't boot when it's attached. I unplug it, and the computer works fine.
 
I do not know the details of why this happens, I'm still learning when it comes to hardware, or maybe this is just a special case. I'm not sure. But I know that whether my computer boots or not depends on whether that device is plugged in. I have yet to remove it, due to laziness, but it's just unplugged from the mother board.

---

### Post by Bucky Ball on 2011-07-11
If it is under warranty I'd take it straight to a service centre before you do something with your hardware that voids your warranty, like removing/replacing/fiddling with hardware. Not my idea; some companies are pretty hardcore about this issue. Save yourself some time and stress if it's covered. HP was it? Generally courier pick up and return (I used to have HP DV6000). ;)

---

### Post by ajsoulmate on 2011-07-11
> **Bucky Ball said:**
> If it is under warranty I'd take it straight to a service centre before you do something with your hardware that voids your warranty, like removing/replacing/fiddling with hardware. Not my idea; some companies are pretty hardcore about this issue. Save yourself some time and stress if it's covered. HP was it? Generally courier pick up and return (I used to have HP DV6000). ;)

Unfortunately, it is NOT under warranty anymore :(

Yes, HP Pavilion DV5.

---

### Post by ajsoulmate on 2011-07-11
> **FormatSeize said:**
> A bad hard drive shouldn't cause anything else to fail. Something I just thought of, though, try taking out or unplugging the optical drive. 

Why would I unplug the Optical Drive if there is nothing inserted anyway? as I mentioned previously, she doesn't have another machine to create a LiveCD or even a LiveUSB.

Everything was working probably. She downloaded Ubuntu 10.04 64-bit and we were discussing what to do next, etc. Then, the laptop started to restart all by itself.

She confirmed that she has that restart issue before but it happened 2-3 times a day MAX. Last night was horrible. While I was with her over the phone, the laptop was restarting then shutting down every 1-2 mins.

She tried to burn a CD before this but the CD/DVD Drive couldn't detect the Blank CD.

When I suggested to use USB instead, the laptop couldn't detect the USB Drive :/

> When my other computer failed, I kept parts of it like the HDD and optical drives. The CD drive from my old computer works well. But then I replaced it with an additional DVD drive, and my computer won't boot when it's attached. I unplug it, and the computer works fine.
 

I think it's a bit different with Laptops.

> I do not know the details of why this happens, I'm still learning when it comes to hardware, or maybe this is just a special case. I'm not sure. But I know that whether my computer boots or not depends on whether that device is plugged in. I have yet to remove it, due to laziness, but it's just unplugged from the mother board.

When it comes to Laptops, I feel like I know nothing. This is the 2nd weird case I have ever seen in few months. One was with Dell. It was for a friend who asked for my help. I couldn't do anything so laptop went to maintenance or someone who fixed it.

This time, it's even more strange.

I suspected the heat could be effecting the over all performance and/or functionality of the laptop but it was NOT that hot.

They keep producing cheap lousy laptops that won't last more than 2-3 years. I do have an HP laptop since 1998 and it is WORKING until now.

---

### Post by MlDean on 2011-07-11
i have did a couple of buggy installs , but nothing as bad as what you are describing , all it required was downloading a different version of Ubuntu or just reinstalling the one i had , if the pc was working fine before the install of 10.04, i would  either install 11.04 or try to system restore the windows if its still on there , to see if the problem is still there , you didn't mention what CPU the laptop had , Intel  claims that there are some Intel CPUs that are not compatible with Linux , most notably some of the Core series , in the core series the OS controls the CPU smart functions , voltages, Multiplier  , etc, they claim that the v core voltage can drop when using a non approved OS causing instability and damage , now i am not sure if i believe this or not, i have built 2 core series PC's , a Core I 7  and a core 2 duo , and  all the CPU and memory functions were adjustable through the BIOS , and did not seem to even need a  OS to function , except for a couple of exceptions to the rule , Ubuntu seems to be a very stable , use-able OS ....

---

### Post by BeaverDono on 2011-07-11
> Why would I unplug the Optical Drive if there is nothing inserted anyway? as I mentioned previously, she doesn't have another machine to create a LiveCD or even a LiveUSB.

If that is even possible unplugging the optical drive from the motherboard, most likely its soldered on if its a laptop.

> 
While I was with her over the phone, the laptop was restarting then shutting down every 1-2 mins.

Is this while its booting up Windows or sitting? 

> When I suggested to use USB instead, the laptop couldn't detect the USB Drive.

While Windows is loaded? Or when its booting? With a LiveUSB you should be able to boot directly from the USB if your motherboard/BIOS supports that feature. One way to check is the boot priority and if you can switch the listing to something along these lines..

1. USB/Thumb Drive
2. CD - (Should have tons of details about the optical drive)
3. HDD 


> I suspected the heat could be effecting the over all performance and/or functionality of the laptop but it was NOT that hot.

Laptops can get pretty hot, if all else fails, throw it in the freeze. Sounds stupid but if you chill it off.. MAYBE 10 to 20 minutes, you might get a bit more extended life out of them. When dealing with hard drive failures, a popular method was to stick them in a zip lock baggy and freeze them for 30 or so minutes and pop the drive back in. You would only get anywhere from 2 to 5 minutes but it would be enough to remove data from the drive itself.


-----------------

If you have access to another computer (a friends, your own, etc..)

LiveCDs are fine if the optical drive is working but as you stated earlier that is a no go. So I would grab a thumb drive, head over to a friend's computer and download yourself a copy of the Ubuntu or any Linux Distro she would like to use. 

There is a ton of tutorials out on the internet that can walk her through making a LiveUSB install. My personal gurus I like to turn to is [PenDrive Linux]("http://www.pendrivelinux.com") since I used them when my laptop went belly up. 

One note before slapping on a LiveUSB of your distro, format the thumb drive to a FAT32 configuration since the majority of distros will **read** and write to a FAT32 drive. NTFS has become a bit more popular in the Linux community and I know some of the newer version of Ubuntu (Ubuntu 10.10+ at least) are compatible with reading and writing to a NTFS configuration. 

Once you get that LiveUSB working, you should be able to recover some data from the hard drive as long as it functioning. When you do install from the LiveUSB, format that drive so you can have a healthy partition to work with your Linux Distro you've picked.

---

### Post by ajsoulmate on 2011-07-12
> **MlDean said:**
> i have did a couple of buggy installs , but nothing as bad as what you are describing , all it required was downloading a different version of Ubuntu or just reinstalling the one i had , if the pc was working fine before the install of 10.04, i would  either install 11.04 or try to system restore the windows if its still on there , to see if the problem is still there , **you didn't mention what CPU the laptop had** , Intel  claims that there are some Intel CPUs that are not compatible with Linux , most notably some of the Core series , in the core series the OS controls the CPU smart functions , voltages, Multiplier  , etc, they claim that the v core voltage can drop when using a non approved OS causing instability and damage , now i am not sure if i believe this or not, i have built 2 core series PC's , a Core I 7  and a core 2 duo , and  all the CPU and memory functions were adjustable through the BIOS , and did not seem to even need a  OS to function , except for a couple of exceptions to the rule , Ubuntu seems to be a very stable , use-able OS ....

Apparently, you did not read my first post :(

---

### Post by mastablasta on 2011-07-12
> **ajsoulmate said:**
>  
If so, then there is NO BEEPS when we removed the RAM or when one of the chips was inserted.
 
 
Time to check the manual then.. If you dont' have it the HP site has usually a PDF verison. However in desktops no beep is no good. it indicates that motherboard failed to initialise self-test and confirm that all is good (one short beep = all good) this could explain your problems and perhapos a "simple" motherboard change will make it all work again. now when i say simple i mean simple for the HP service :-)
 
I had a motherboard it stopped working in little over a year. same motherboard on another compuiter worked so i replaced it with that one and after 5 years it still works OK. sometimes you just have bad luck... maybe it was made on Monday :-)
 
 
>  
 
If she just had a backup for her files, we would have done a system recovery which already comes with the laptop and if that did not help, we can format.
Now, we just need to take the info out then we can do whatever we want.
  
 
If motherbaord is faulty then data should be OK. the only way to protect the data is to unplug the hard disk (if that is even possible) and plug it into another computer and then download the data form it. possibly erase the disk (overwrite with zeroes) and format the system partition (not recovery one). 
 
>    
That's the thing. She needs another machine in order to create a LiveCD or LiveUSB. That laptop is the only machine she got and I'm too far from her. Hope she can find another machine with some friends or family. That's the only option rather than sending it to service and God knows what will they do ... they may format it and she'll lose all her stuff. 
 
it's a bummer indeed. when it happened to me i made numerous data backup CD , clonezilla Cd etc etc... :-) but i too didnt' have it before. had to make one at work. but i learned something tha day. its' good to have a live CD handy. and now that my CD/DVD writer is acting up i learned that it's also good to have a live USB handy :-)
 
good luck with repair. and i wouldn't be so afraid of professional service . epsecially not HP (i do understand the sensitive date issue).

---

### Post by ajsoulmate on 2011-07-12
Don't ask me how? why? when? :D

I've been talking with her over the phone (because she has no other machine to access the internet and use any messenger) since morning and guess what?

[B]THE LAPTOP IS WORKING NOW O_o
[/B]

We managed to restore the Laptop to it's factory default status and I really do hope it will WORK.

However, the process to restore the Laptop to the factory default setting, it takes much longer than formatting and install Windows again :(

She just want to restore Windows and then she'll try Ubuntu.

God, she gave me a very HARD TIME listening to stupid Windows messages. THANK GOD with Linux, I don't have to read these things.

Thank you everyone and will keep you updated about what will happen to us.

I'm happy because she doesn't have to buy new one, at least for now :D

---

### Post by Bucky Ball on 2011-07-12
Good news. Please mark as 'solved' and post a new thread if you need to. ;)

---

### Post by ajsoulmate on 2011-07-12
> **Bucky Ball said:**
> Good news. Please mark as 'solved' and post a new thread if you need to. ;)

Yes, it's :) we've been so sad for the last two days.

Not now. We'll keep monitoring the Laptop and once everything will be okay and NO MORE restart or shut down, I'll mark this thread as solved :)

Thank you :)

---

### Post by Swagman on 2011-07-12
That smacks of a dry joint somewhere.

Put the lappie on the table and  *Don't move it !!*

---

### Post by walt.smith1960 on 2011-07-12
I'm glad to hear you got the machine working again but something on the first page raised a red flag to me.  When you removed one memory module and the machine worked properly and when you reinserted and removed the other memory module it didn't.  That sure sounds like either a memory module (SODIMM) or socket problem.  If this happens again (and I hope it doesn't), I'd try the memory module that works in both sockets.  if one module works in both sockets, the sockets are most likely okay.  You could try the other module and see if it messes up In both sockets.  If it does, you most likely have a bad SODIMM.  If the machine is working now, you could run memtest86+ for an extended period of time--2 hours +--and see if there are errors there.  It'd be a shame to spend $$ on repairs when the problem is a bad $25 SODIMM.

---

### Post by ajsoulmate on 2011-07-12
> **walt.smith1960 said:**
> I'd try the memory module that works in both sockets.  if one module works in both sockets, the sockets are most likely okay.  You could try the other module and see if it messes up In both sockets.  If it does, you most likely have a bad SODIMM.

I asked my girl over the phone to do something she has never done in her entire life so it wasn't easy at all. However, she managed to do what I asked her to do.

We already did that.

1- She removed all RAM Chips

2- She inserted one of the RAMs in Socket 1

3- The laptop worked perfectly.

4- She removed RAM 1 and inserted RAM 2 in the same Socket. The laptop DID NOT WORK.

5- She removed RAM 2 and inserted it in the other socket and the same happened, the laptop did not work.

6- When she inserted RAM 1 into both Sockets, the laptop did not work.

7- We have tried ALL the possible scenarios for that but nothing happened.


> 
If the machine is working now, you could run memtest86+ for an extended period of time--2 hours +--and see if there are errors there.  It'd be a shame to spend $$ on repairs when the problem is a bad $25 SODIMM.

That is exactly what I'll ask her to do once she arrives home because she's at work now.

She had to leave for work today so we couldn't run the memory test. Hope we'll do that tonight. After all, I'm giving her these instructions remotely. It's fun but headache :(

Thank you :)

---

### Post by Bucky Ball on 2011-07-12
You're doing a good job, both of ya. ;)

With the memtest, it takes hours if you go all the way, so setting it going before going to work would be fine.

---

### Post by ajsoulmate on 2011-07-13
> **Bucky Ball said:**
> You're doing a good job, both of ya. ;)

With the memtest, it takes hours if you go all the way, so setting it going before going to work would be fine.

Appreciate that :)

Hopefully we'll do it today. I'll report back the result and I do hope there is nothing wrong with the RAM and it was just a Windows (Software) issue.

LiveUSB is ready and I asked her to keep it somewhere safe.

CD/DVD Drive doesn't work still. She never used it. Not sure why it stopped working?

Hopefully we can install Ubuntu today on USB Drive. That would be the first step. If everything will be fine, then definitely a Hard Drive installation is required :)
The only problem I'm concerned about is the Graphics Card :/
She got nVidia Geoforce 9600 if I'm not wrong. Let's see what will happen when we'll run the LiveUSB.

---

### Post by Bucky Ball on 2011-07-13
LiveUSB will probably use the default Ubuntu drivers. Nvidia drivers won't install unless you install them from System>Administration>Additional Drivers. They will be offered there, just don't do anything for now (as they would have nowhere to install if you are booting from the LiveCD/USB, if you get my meaning). ;)

Once you have Ubuntu installed on the hard drive you can try then. If it kills graphics, boot to the recovery kernel, choose 'Failsafe X' from the options which eventually appear. That will get you to a desktop with low-graphics mode, and you can switch the Nvidia drivers off again and look for a fix or just use whatever free drivers are being used already (which you will default to when there is no Nvidia driver installed).

---

### Post by ajsoulmate on 2011-07-14
Could you help me please :)
I'm confused and not sure whether my machine is 64 or 32 bit ??



[http://h10025.www1.hp.com/&#8203;ewfrf/wc/document?docname=&#8203;c01571758&tmp_task=prodinf&#8203;oCategory&cc=emea_middle_e&#8203;ast&dlc=en&jumpid=hpr_R100&#8203;2_EMEA_MIDDLE_EASTEN&lang=&#8203;en&lc=en&product=3807984](http://h10025.www1.hp.com/&#8203;ewfrf/wc/document?docname=&#8203;c01571758&tmp_task=prodinf&#8203;oCategory&cc=emea_middle_e&#8203;ast&dlc=en&jumpid=hpr_R100&#8203;2_EMEA_MIDDLE_EASTEN&lang=&#8203;en&lc=en&product=3807984)



[http://ark.intel.com/Produ&#8203;ct.aspx?id=35562](http://ark.intel.com/Produ&#8203;ct.aspx?id=35562)

---

### Post by nynoah on 2011-07-14
> **ajsoulmate said:**
> Could you help me please :)
I'm confused and not sure whether my machine is 64 or 32 bit ??



[http://h10025.www1.hp.com/&#8203;ewfrf/wc/document?docname=&#8203;c01571758&tmp_task=prodinf&#8203;oCategory&cc=emea_middle_e&#8203;ast&dlc=en&jumpid=hpr_R100&#8203;2_EMEA_MIDDLE_EASTEN&lang=&#8203;en&lc=en&product=3807984](http://h10025.www1.hp.com/&#8203;ewfrf/wc/document?docname=&#8203;c01571758&tmp_task=prodinf&#8203;oCategory&cc=emea_middle_e&#8203;ast&dlc=en&jumpid=hpr_R100&#8203;2_EMEA_MIDDLE_EASTEN&lang=&#8203;en&lc=en&product=3807984)



[http://ark.intel.com/Produ&#8203;ct.aspx?id=35562](http://ark.intel.com/Produ&#8203;ct.aspx?id=35562)

Links broken

---

### Post by ajsoulmate on 2011-07-14
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01571758&tmp_task=prodinfoCategory&cc=emea_middle_east&dlc=en&jumpid=hpr_R1002_EMEA_MIDDLE_EASTEN&lang=en&lc=en&product=3807984](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01571758&tmp_task=prodinfoCategory&cc=emea_middle_east&dlc=en&jumpid=hpr_R1002_EMEA_MIDDLE_EASTEN&lang=en&lc=en&product=3807984)


[http://ark.intel.com/Product.aspx?id=35562](http://ark.intel.com/Product.aspx?id=35562)

---

### Post by Bucky Ball on 2011-07-15
System>Preferences>System Monitor. That should tell you what you want. If it's dual-core, it's 64.

* Forget that; this is right from the second link you posted, quite plainly there:

> Instruction Set: 64-bit


Even more obvious further down that page is:

> Intel 64: Yes

Plain as day.

Please read your research thoroughly before posting. ;)

---

### Post by ajsoulmate on 2011-07-15
> **Bucky Ball said:**
> System>Preferences>System Monitor. That should tell you what you want. If it's dual-core, it's 64.

* Forget that; this is right from the second link you posted, quite plainly there:



Even more obvious further down that page is:



Plain as day.

Please read your research thoroughly before posting. ;)



Hi, thank you so much for your support and help. Believe me, I CAN read but it's just that I was confused. It's true that Intel's Website shows my CPU is 64-bit but I have no idea the OS is 32-bit :/ Oh well, sooner or later, I'll get rid of Vista once and for all. Thanks again!

---

### Post by Bucky Ball on 2011-07-16
To check what your machine is running:

System>Admin>System Monitor. ;)

---

### Post by ajsoulmate on 2011-10-04
I'm sorry for the late reply.

I have had a very interesting experience with my HP Laptop.
This laptop is simply dying slowly and has hardware issues but I managed to install Ubuntu 10.04 and OMG there is HUGE difference between Vista and Ubuntu. I'm very happy with it and I wish I could have used Linux before but as they say, never too late and better late than never.

Thanks everyone!

---

### Post by Bucky Ball on 2011-10-05
What model is it (sorry if you have already mentioned)? My HP died a slow death and then I discovered it was a known issue and HP was repairing for nothing all those models still within 24 months of purchase date. Mine was about 26 when all this started happening and I had a battle royale with HP (which I lost in the most disheartening and disgusting manner as they basically wiggled out of it but were legally able to do so).

---

### Post by ajsoulmate on 2011-10-07
> **Bucky Ball said:**
> What model is it (sorry if you have already mentioned)? My HP died a slow death and then I discovered it was a known issue and HP was repairing for nothing all those models still within 24 months of purchase date. Mine was about 26 when all this started happening and I had a battle royale with HP (which I lost in the most disheartening and disgusting manner as they basically wiggled out of it but were legally able to do so).

HP Pavilion dv5.
Problem started few months ago. Windows Vista wasn't responding and then over heating problem started at the same time.
That's why I started this thread few months ago, I was unable to do anything.
In fact, Ubuntu came as a rescue and after I installed it, it fixed my Windows issue. Windows was NOT BOOTABLE whatsoever. I even failed to do recovery.
Now, I'm afraid my HP is dead ... I still can turn it on though but ... it stays ON for 5 mins no matter what I do, even if I do nothing, it's just 5 mins then it's off.
I hate HP :/

It's a black screen and nothing else.

Have you experienced the same issue?

---

### Post by ajsoulmate on 2011-10-07
Ok, looks like we are back to square zero. My laptop now is acting crazy again. I can enter BIOS, do whatever I want on BIOS but after 5 mins, it's OFF.
 Any idea? is there anyway I could solve this without buying a new one because ... I'm jobless at the moment :(

---

### Post by wackawacka on 2011-10-07
> **ajsoulmate said:**
> Ok, looks like we are back to square zero. My laptop now is acting crazy again. I can enter BIOS, do whatever I want on BIOS but after 5 mins, it's OFF.
 Any idea? is there anyway I could solve this without buying a new one because ... I'm jobless at the moment :(



i've been fixing computers for 15 years and i haven't met a machine i couldn't fix.  so it is possible to fix any computer and i don't promote unnecessary purchasing of new machines to my clients and my clients are grateful for that.   

when motherboards fail, you usually see a domino effect of problems because with laptops, the motherboard integrates many parts.  

i've seen your problem before with two computers that randomly shutdown and they were both HP's.  

re-seating always helps.  you re-seated the ram, but you should also re-seat the hard drive.  

but, what solved my client's problems was two things: power supply and power strip.  

if you have a power strip with bad ground, it'll affect your laptop's power supply sending incorrect signals that will affect voltage/current sensitive components.  in both cases i saw, replacing the power supply ($40) and changing the power strip ($3) fixed these issues.  

after doing these steps, you must go into the bios and reset all settings to default, save, reboot and then change the settings to what you like.  

gl!


i just remembered, last year, another client had the same issue and it was HP as well, that client needed the above as well as a new hard drive and her issue was resolved, no more random shutdowns.  

take care.

---

### Post by ajsoulmate on 2011-10-07
> **wackawacka said:**
> i've been fixing computers for 15 years and i haven't met a machine i couldn't fix.  so it is possible to fix any computer and i don't promote unnecessary purchasing of new machines to my clients and my clients are grateful for that.   

when motherboards fail, you usually see a domino effect of problems because with laptops, the motherboard integrates many parts.  

i've seen your problem before with two computers that randomly shutdown and they were both HP's.  

re-seating always helps.  you re-seated the ram, but you should also re-seat the hard drive.  

but, what solved my client's problems was two things: power supply and power strip.  

if you have a power strip with bad ground, it'll affect your laptop's power supply sending incorrect signals that will affect voltage/current sensitive components.  in both cases i saw, replacing the power supply ($40) and changing the power strip ($3) fixed these issues.  

after doing these steps, you must go into the bios and reset all settings to default, save, reboot and then change the settings to what you like.  

gl!


i just remembered, last year, another client had the same issue and it was HP as well, that client needed the above as well as a new hard drive and her issue was resolved, no more random shutdowns.  

take care.

okay as you suggest i re-seat the ram and re-seat the hard drive and i replace the power strip and i have another HP power supply so i use it and i do the Bios stuff ..save .. reboot but nothing happened :/

---

### Post by wackawacka on 2011-10-08
> **ajsoulmate said:**
> okay as you suggest i re-seat the ram and re-seat the hard drive and i replace the power strip and i have another HP power supply so i use it and i do the Bios stuff ..save .. reboot but nothing happened :/

i'm interested in this problem haha.  what do you see?  give me a picture of "nothing happened"

also, check to make sure the voltage and amperage match your specific power supply.  electronics hate differences in current.  sometimes you can get away with differences in voltage, but more down than up and if the wattage is big, then belay my last.

---

### Post by ajsoulmate on 2011-10-08
> **wackawacka said:**
> i'm interested in this problem haha.  what do you see?  give me a picture of "nothing happened"

also, check to make sure the voltage and amperage match your specific power supply.  electronics hate differences in current.  sometimes you can get away with differences in voltage, but more down than up and if the wattage is big, then belay my last.

Thank you Mr.Waka for your interest in my case :)
Nothing <means> .. When I plug in my computer show me the screen labeled HP which I can access from it on the set up menu , then a black screen shows nothing but black screen :/
Regarding the issue of Electric power I checked again and everything is ok !!

---

### Post by wackawacka on 2011-10-08
> **ajsoulmate said:**
> Thank you Mr.Waka for your interest in my case :)
Nothing <means> .. When I plug in my computer show me the screen labeled HP which I can access from it on the set up menu , then a black screen shows nothing but black screen :/
Regarding the issue of Electric power I checked again and everything is ok !!

before i want to think about whether an operating system is installed or not, go into the bios and make sure the computer reads a hard drive.  you should see a model (maxtor, seagate, etc) and size of hard drive presented on your screen in the bios (press either F2 or F10 or F12, probably F12, many systems are different but these are the choices).  

assuming the hard drive is there and we can move on to whether the operating system is preset, do this...

1.  immediately after the HP logo, press F8 a bunch of times. 

this is a simple test to tell me whether or not you have an MBR pointing towards windows.  if your system knew how to get to windows, you should see access to safe mode.    

it still doesn't tell me if you have an MBR at all, but it's a good start.  

2.  assuming that fails and the goal is to get your windows up and running because the ubuntu experience put you here, grab a windows cd, boot into the cd (check bios make sure CD boots before hard drive), select the "Recovery" option when you see it.  you will be taken to a terminal... type this:  

fixmbr

this is what i do to remove grub and/or fix the master boot record (mbr) which allows the computer to know what to do next after loading the bios.  

i think this may be the confusion your laptop is facing...  with what you have given me, this is where i would start.  

i'm interested in knowing if you can get to the last step without hiccups and what happens next.  

i'm also interested in knowing what those hiccups might be when you run into them.  


something is bugging me.  usually, if you have no MBR, the machine tells you.  you haven't reported that problem.  heck, the machine would tell you if it didn't pick up a hard drive, but do that check step in the bios anyway.

so what i'm getting at is i'm curious what you did while in the ubuntu installation.  what did you do at the partition section?  some of the clues kind of sound like a partition or partitions were removed.  

i can see a scenario where the windows partition is removed, but you won't get an MBR message because grub is still hanging around, even after you deleted the linux partition.  

that can happen and it sounds like your issue as of right now until i see your feedback.  

so do those steps, understand where i'm at and think about it for your machine and let's see what happens.  

gl!

---

