---
title: "Twins one is fine"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-06-13
I have two new identical computers one 9.04 installed fine. I decided to convert the other to 9.04 as well. Both are AMD Athlon™ single-core processor LE-1620; 2GB DDR2 memory; DL DVD±RW/CD-RW drive; Labelflash technology; 160GB hard drive; Windows Vista Home Basic with SP1.

The second one will not install. It goes so far and then the screen goes dark the cursor flashes ,and then it goes dark and the cd drive goes silent.
I have tried running it live or just plain install which is what I want. I checked the bios it's fine. I am at a loss as what to do next.

---

### Post by jbruced on 2009-06-13
This is just a shot in the dark.

As I'm sure you know, its either a different PC bios setup, slightly different components within the PC, the CD drive won't read as well as the other(maybe a little different alignment), or the CD can't be read as well due to dirt or scratches.

Have you tried going into the bios and resetting to defaults before trying?

GL
Bruce

[EDIT] 
Next step may be to burn the Ubuntu install CD on the second PC, this will assure the head is lined up correctly to read.

---

### Post by rosswmcgee on 2009-06-13
Yes and I did check the CD found no errors and used a spare as well. I note that trying it with the wubi exe it asks for my password but does not accept it for some reason. But all the attempts have been with a cold boot. Ha! wubi says this computer will not boot from cd? installing cd boot helper. After installing cd boot helper, apparently a shell of Ubuntu is on the computer. On boot up I can choose between vista or ubuntu. Choosing ubuntu just leaves me with a ubuntu screen with the line going back and forth. Now I am using windows system restore. I have never had this much problem with an Ubuntu clean install.

---

### Post by s.fox on 2009-06-13
Hi,

Can you please post the exact error message from WUBI.

Thanks,

Ash R

---

### Post by rosswmcgee on 2009-06-13
It just said this computer will not boot from CD. Install cd boot helper. Remember this is Vista talking, not Ubuntu.

---

### Post by rosswmcgee on 2009-06-13
Just tried another clean install. The music plays but the screen goes dark and then the cd goes quiet.

---

### Post by ddrichardson on 2009-06-13
Check the machines have the same BIOS release because it sounds like an APIC implementation issue.

---

### Post by rosswmcgee on 2009-06-13
I am not sure what apic is and unsure on how to see the diff in the bios release? Even so what is the fix or am I stuck with windows vista on one machine?

---

### Post by donkyhotay on 2009-06-13
Are you using the liveCD? If so can you run the memtest? Might be a bad RAM chip (though this is another shot in the dark). How far through the install process does the computer get?

---

### Post by rosswmcgee on 2009-06-13
It got about half way. It is on the computer because upon boot I get a choice, even though I did not opt for dual boot. I am at a loss because I prefer ubuntu. I may try an 8.10 install.

---

### Post by ddrichardson on 2009-06-13
> **rosswmcgee said:**
> I am not sure what apic is and unsure on how to see the diff in the bios release? Even so what is the fix or am I stuck with windows vista on one machine?Just go into BIOS and find the version numbers.

APIC is one of the power management standards and is quite prone to odd implementation which is controlled in BIOS and a common symptom is a blank screen while everything else works.

You can do one of two things if it is - flash the BIOS to the same state as the one that works, or add the word noapic to the end of the kernel boot line.

There's no point in floundering around with shots in the dark. Check the BIOS versions, check the hardware is the same (if it isn't then we can discuss the differences for known issues).

Memory errors are usually detected on Power On Self Test (POST) and generally a bad RAM chip will cause a system to crash because the fetch/execute cycle has been interrupted.  This isn't what you describe.

Also, you mention the machines are the same - are they the same manufacturer and model number? I 'd also check the mainboards are the same model.  When you go to Dell and demand a hundred machines on a business account, they'll strive to give you identical machines but this isn't true of home systems because the market fluctuates too much and so there are often differences between machines.

---

### Post by Sinkingships7 on 2009-06-13
A lot of stopped installs are due to bad RAM. You should run a memory test on both and compare the results.

---

### Post by rosswmcgee on 2009-06-13
When I try the live CD, I get as far as the Ubuntu sign in music, just before the music the screen goes dark, so I can not proceed. I ran a system check on the vista and a chkdsk and all was well. Vista itself works fine. Stumped. it appears to me the bios is the same.

OK here is my solution to the problem which is not a problem now. I booted from the CD pressed F10 then F4
and selected Safe MODE. The install worked perfectly. Go figure? I hope this may help some one else with the same problem. Thank you very much every one for all of your suggestions, and for taking the time to work on it. I now have three 9.04 computers. I am an Ubuntu fan, I am amazed at the ease of over all operation as compared to other systems. I played around a week with Vista, fooooooooogetabout it! lol

---

