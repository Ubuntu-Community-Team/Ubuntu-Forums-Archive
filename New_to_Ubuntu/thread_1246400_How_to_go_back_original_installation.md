---
title: "How to go back original installation"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Mauricioso on 2009-08-21
Using Ubuntu 9.04 in dual boot with Win XP, I've been learning about sudo and made some mistakes. Is there a way to go back to the orignal state of Ubuntu, or repair it, without having to make a clean install? 
Thanks :P

---

### Post by presence1960 on 2009-08-21
what mistake(s) have you made? Please be specific.

---

### Post by auddin2 on 2009-08-21
If you end up having to do a clean install, you should make a separate home partition as described here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
When you do the re-install, you can then specify your home partition as the home directory.
That way if you ever want to re-install or try a different release, your settings (that will be saved in your home directory) will remain the same because your home partition will remain untouched.

---

### Post by Mauricioso on 2009-08-24
To answer Presence 1960 I cannot tell exactly what the mistakes I made are, I tried so many things but do you know if it is possible to go back to the original state of Ubuntu by repairing it via the CD like in Window XP (even if it means lost of home files)?

---

### Post by SOULRiDER on 2009-08-24
AFAIL all you can do is reinstall. You have your hard drive already partitioned though, so installation shouldnt take more than 15 minutes.

---

### Post by Mauricioso on 2009-08-24
What do I choose when the install ask what partition to use for Ubuntu? I got the 3 standard ones, Swap, Root and home, should I choose all 3 of them?

---

### Post by SOULRiDER on 2009-08-24
You need to select a swap partition (should be done automatically) and a root partition. Home is optional.

As long as you set a / (thats root) partiton youre good to go.

---

### Post by mikewhatever on 2009-08-24
Well, the swap partition is usually autodetected, so that you'll only need to specify root and home.

---

### Post by Rrory on 2009-08-24
I have  a dual boot too. I love Ubuntu and just keep windows for a few programs.
  Well, windows crashed and died while Ubuntu is working fine. So I now have a dilemma. Should I take my old Sony Vaio S series to the shop and have them reload XP. Or is it just cheaper to get a windows netbook and devote my Vaio entirely to ubuntu?. I also have a linux netbook that I love. *sigh*  I need google talk, Word and use Cyberpad. that's it. 
   I really appreciate the advice. Ubuntu is so stable and wonderful...

oh on thing, I have Opera in Ubuntu and sometimes it stalls, I cannot type, is this due to some nasty Windows bug?

---

### Post by gordintoronto on 2009-08-24
> **Rrory said:**
> I have  a dual boot too. I love Ubuntu and just keep windows for a few programs.
  Well, windows crashed and died while Ubuntu is working fine. So I now have a dilemma. Should I take my old Sony Vaio S series to the shop and have them reload XP. Or is it just cheaper to get a windows netbook and devote my Vaio entirely to ubuntu?. I also have a linux netbook that I love. *sigh*  I need google talk, Word and use Cyberpad. that's it. 
   I really appreciate the advice. Ubuntu is so stable and wonderful...

oh on thing, I have Opera in Ubuntu and sometimes it stalls, I cannot type, is this due to some nasty Windows bug?

Word should work fine under Wine, if you really can't use Open Office.

Pidgin can talk to Google Talk, according to Google.

---

### Post by marshmallow1304 on 2009-08-24
> **Rrory said:**
> I need google talk

Pidgin supports Google Talk.


Edit: Oops, didn't see gordintoronto's post.

---

### Post by Mauricioso on 2009-08-24
And do I have to specify again  'Iinstall boot loader' at the end?

---

### Post by louieb on 2009-08-24
> **Mauricioso said:**
> And do I have to specify again  'Iinstall boot loader' at the end?
Yes.

---

### Post by Rrory on 2009-08-24
Gord;
   that's just so helpful, I'll check out pidgin. I love Open Office.  My problem is I use a digital notepad, so I upload my handwriting and change it to text and it only works with windows bleah. Linux doesn't support this yet or yeah I'd totally be 100% linux. I can't use Wine for that can I?
 thanks again
Courtney

---

### Post by gordintoronto on 2009-08-25
> **Rrory said:**
> Gord;
   that's just so helpful, I'll check out pidgin. I love Open Office.  My problem is I use a digital notepad, so I upload my handwriting and change it to text and it only works with windows bleah. Linux doesn't support this yet or yeah I'd totally be 100% linux. I can't use Wine for that can I?
 thanks again
Courtney

I went and looked at the information about the Cyberpad.  Sorry, I doubt if its software will work under Wine.  If I were you, I would put about 10 minutes into trying it, and if that fails I wouldn't push it.

My (Chinese) wife uses a tablet for entering Chinese text into Windows, and I would be astonished if that software would work under Wine.  The result: she is stuck with Windows.  Any time my machine is busy and I try to use hers, I get terribly frustrated.

---

### Post by Rrory on 2009-08-26
wow, much appreciated Gordon. that's a great help. Thank you so much!
 My folks use Windows and I just may use their computer for my cyberpad. When I finish writing for the day, just upload,  change to text and store everything on my flash drive. 

I'll get rid of the partition and devote my laptop entirely to Ubuntu. One thing,  Is Office compatible with Word? It's not a big issue with me as I write by hand...but I'm wondering if I can plug my flashdrive in my laptop and edit my novel in Office and then save it back into a Word file...

---

### Post by gordintoronto on 2009-08-26
> **Rrory said:**
> Is Office compatible with Word? It's not a big issue with me as I write by hand...but I'm wondering if I can plug my flashdrive in my laptop and edit my novel in Office and then save it back into a Word file...

In my experience, the compatibility is imperfect.  OO can open and save DOC files, but if they have complex formatting, they won't look right.  (Often, they don't look right on a different computer which uses the same version of Word but has a different printer or a different page format.)  For simple text files it should be just fine.

I'm not sure what the current status is for DOCX files.

---

### Post by Rrory on 2009-08-29
Okay,many thanks Gordon;
 hmm, I realize now that I need either to split my hardrive again and dedicate part of my computer to the Windows programs I need. Or maybe get a separate cheap netbook with Windows.  
     I got rid of the partition, and I don't know if its hard for a non-techhie like me to put one in...sigh my old laptop is running so fast with only Ubuntu, it's a dream.

---

