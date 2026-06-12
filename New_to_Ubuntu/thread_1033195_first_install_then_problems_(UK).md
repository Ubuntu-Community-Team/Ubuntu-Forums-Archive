---
title: "first install then problems (UK)"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by candtalan on 2009-01-07
I am helping a non techie friend, using email (in another forum) who wants to get started with Ubuntu. He has used a CD from a magazine, available in UK, ComputerActive 'Ultimate guide to Linux' which I think is this:
[http://www.computeractive-direct.co.uk/index.cfm?p=16&itemid=2946](http://www.computeractive-direct.co.uk/index.cfm?p=16&itemid=2946)
I see that 8.10 is used.

I paste below a version of his comments and I would be grateful for any comments here. I note that his comments say he rebooted with the computeractive CD, although I had previously been encouraging the use of the wubi facility which is I think also available on the CD. I am not exactly sure (yet) if wubi was used here. It sounds as if he is using a PC with Windows preinstalled on a single large hard disk

================
I installed and read the ‘computeractive’ CD (in windows that is), and did as it said and rebooting with the CD in the tray. Everything went great, then, as you know, my cousin came just as I did this, so I only had a chance to sort of have a look round. Later on, I used windows to do some e-mails and write a letter, did no more yesterday.
Today, because I had a couple of letters to do, I thought it a good opportunity to get some practice. The set-up I have is, on start-up, it gives me a choice of windows or ubuntu. I take it that it has created a partition on the HD. When I started to-day, first thing was the updates.. I did the download.. which took quite a time. It then showed me the message that there were four faults, and as there was no information what to do I decided to carry on. Then I tried to open the ‘open office’ word programme.. which remained a small window in the centre of the screen which I could not maximise, so I tried with others – same result.. couldn’t maximise anything. Then i got a message that it was write only.. as l hadn't a clue I decided to reboot to see if that helped – that's when I got the black screen telling me of the faults, I think it was saying that it had tried to do something but failed, so a manual fsck was to be performed. I rebooted a couple of times, but got the same thing – that's when I chickened out. Can you make any sense of this? – and I am grateful for (help)
================

(the 4 faults were I guess, 4 update connections that were not available at that time. I do not know if a reboot is important following the initial updates after 8.10 install, because it sounds like he used OO.o (or tried) before later rebooting and then geting a fsck related error)

comments appreciated

---

### Post by hyper_ch on 2009-01-07
without knowing what those "faults" are one cannot help.

---

### Post by Tomatz on 2009-01-07
Why not direct him to this thread? It would be a lot easier to help him ;)

---

### Post by candtalan on 2009-01-07
> **hyper_ch said:**
> without knowing what those "faults" are one cannot help.
They are very likely to be 4 of the 170 or so updates that failed to get connected. When I have been doing updates over the years, I see that occasionally  not all are successful on a first occasion. 

1) are there likely to be problems as found here simply because a few updates have not come down?

2) Could the lack of a reboot following certain updates give this type of trouble? It is likely that the first 170 updates to date after 8.10 install will have included at least one kernel update(?) If so a reboot symbol would have been shown, but this very novice user obviously did not see this and continued to use the machine (OO.o) and found what seemed like trouble. A manual fsck request implies a damaged file system and all this guy has hardly used the system as far as I can gather.

---

### Post by candtalan on 2009-01-07
> **Tomatz said:**
> Why not direct him to this thread? It would be a lot easier to help him ;)
He will be here in good time. 
Just now he is not likely to be comfortable enough with a forum such as this yet. 

I have many friends and contacts who are elderly. One recent beginner I helped and continue with is an 88 year old lady who had never used a PC before, she now does online shopping, with a bit of help but not much. 

Such novices do not have the methods of disciplined expression and action that this sort of forum needs. The guy who is the subject of this thread is in an old people's forum.

---

### Post by Tomatz on 2009-01-07
I would suggest that he downloads a LTS 8.04 (hardy) .iso and uses that. Intrepid still has compatibility issues and hardy is a LTS (long term support) release. Which would probably better suit his needs as its supported for 3 years rather that 6 months (1 year).

I'm thinking the CD he used had physical defects.

If he isn't confident burning a copy from an .iso, he can buy one here:

[http://www.thelinuxshop.co.uk/catalog/product_info.php?products_id=123](http://www.thelinuxshop.co.uk/catalog/product_info.php?products_id=123)

Its a UK site and it only costs £3.99 + p&p.

---

### Post by hyper_ch on 2009-01-07
what compatibility issues has intrepid? Do you know what compatibility issues has hardy? And you know that LTS doesn't necessarily mean "more stable"? Besides, support on non-lts releases is 18 months ;)

---

### Post by Tomatz on 2009-01-07
> **hyper_ch said:**
> what compatibility issues has intrepid? Do you know what compatibility issues has hardy? And you know that LTS doesn't necessarily mean "more stable"? Besides, support on non-lts releases is 18 months ;)

You are right about the 18 months :mrgreen: but IMO hardy is much more stable than intrepid (at present). When i say compatibility issues i mean bugs with intel and ati gpu's (not necessarily ubuntus fault) and sata problems that pop up on the forums quite frequently. All i suggested was a way the guy could make the transition to ubuntu with minimal fuss ;)

---

### Post by candtalan on 2009-01-08
> **Tomatz said:**
> You are right about the 18 months :mrgreen:  When i say compatibility issues i mean bugs with intel and ati gpu's (not necessarily ubuntus fault) and sata problems that pop up on the forums quite frequently. 
funny you should say such things:
I have just found that my 8.10 installation which I have been using occasionally for months, with regular updates, has suddenly stopped displaying anything. I usually use 8.04 which is on the same machine as dual boot choice.

What this means currently is that I simply cannot use 8.10! It is the subject in another thread, so it need not be solved here, but it does suggest 8.10 might give some problems. I am not a newcomer, and it is certainly giving me problems now!

reference:
[http://ubuntuforums.org/showthread.php?p=6516034#post6516034](http://ubuntuforums.org/showthread.php?p=6516034#post6516034)

---

### Post by bryncoles on 2009-01-08
> **Tomatz said:**
> I would suggest that he downloads a LTS 8.04 (hardy) .iso and uses that. Intrepid still has compatibility issues and hardy is a LTS (long term support) release. Which would probably better suit his needs as its supported for 3 years rather that 6 months (1 year).

I'm thinking the CD he used had physical defects.

If he isn't confident burning a copy from an .iso, he can buy one here:

[http://www.thelinuxshop.co.uk/catalog/product_info.php?products_id=123](http://www.thelinuxshop.co.uk/catalog/product_info.php?products_id=123)

Its a UK site and it only costs £3.99 + p&p.

heck, go here and get the ubuntu cd for free! save yourself £5!

---

### Post by candtalan on 2009-01-08
The person I am helping - he and I are on an older persons forum - has been confident enough to download the iso for a live CD. The main thing was to give him the specific link for the download which was easy for me to do. an deasy ffor him to use. Although he could not at first locate the saved file.

It was interesting that with him being a Windows user, he was strongly attracted towards the environment of the Retail Magazine with CD attached, which had the promise of a grand and easy solution. Perversely, he paid money in a local shop, for the magazine and he got more trouble than if he had simply asked me, and not used the magazine. In many circumstances, the magazine would have been ok. 

However, the magazine CD had application layers above and around the Ubuntu offering, and obviously any slightest problem left him isolated with (me) helper/s not really knowing what his CD had done.

Story to date is that he had in fact done as I had suggested, installed ubuntu into windows via wubi. This meant he could easily uninstall, which he did, and now I (hope) believe he is following a number of detailed steps to burn his new downloaded iso, test it, and then do another desktop iso install via wubi.

Thanks for all responses

---

### Post by candtalan on 2009-01-08
The person I am helping - he and I are on an older persons forum - has been confident enough to download the iso for a live CD. The main thing was to give him the specific link for the download which was easy for me to do. And easy for him to use. Although he could not at first locate the saved file after downloading.

It was interesting that with him being a Windows user, he was strongly attracted towards the environment of the Retail Magazine with CD attached, which had the promise of a grand and easy solution. Perversely, he paid money in a local shop, for the magazine and he got more trouble than if he had simply asked me, and not used the magazine. In many circumstances, the magazine would have been ok. 

However, the magazine CD had application layers above and around the Ubuntu offering, and obviously any slightest problem left him isolated with (me) helper/s not really knowing what his CD had done.

Story to date is that he had in fact done as I had suggested, installed ubuntu into windows via wubi. This meant he could easily uninstall, which he did, and now I (hope) believe he is following a number of detailed steps to burn his new downloaded iso, test it, and then do another desktop iso install via wubi.

Thanks for all responses

---

### Post by candtalan on 2009-01-08
The person I am helping - he and I are on an older persons forum - has been confident enough to download the iso for a live CD. The main thing was to give him the specific link for the download which was easy for me to do. And easy for him to use. Although he could not at first locate the saved file after downloading.

It was interesting that with him being a Windows user, he was strongly attracted towards the environment of the Retail Magazine with CD attached, which had the promise of a grand and easy solution. Perversely, he paid money in a local shop, for the magazine and he got more trouble than if he had simply asked me, and not used the magazine. In many circumstances, the magazine would have been ok. 

However, the magazine CD had application layers above and around the Ubuntu offering, and obviously any slightest problem left him isolated with (me) helper/s not really knowing what his CD had done.

Story to date is that he had in fact done as I had suggested, installed ubuntu into windows via wubi. This meant he could easily uninstall, which he did, and now I (hope) believe he is following a number of detailed steps to burn his new downloaded iso, test it, and then do another desktop iso install via wubi.

Thanks for all responses

---

