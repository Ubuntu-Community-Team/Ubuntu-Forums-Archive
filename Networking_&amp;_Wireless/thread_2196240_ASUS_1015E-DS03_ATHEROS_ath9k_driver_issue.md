---
title: "ASUS 1015E-DS03 ATHEROS ath9k driver issue"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by aquanauta on 2013-12-28
Hi, I've just bought a new ASUS 1015E-DS03 that cames with Ubuntu 12.04 LTS OS pre-installed, but because ASUS sells the same machine with windows 8 it is very probable that they have one HDD image they use for both versions. I say this because my HDD came factory partitioned with 5 partitions, most of them NTFS.
So, I decided to make a fresh install of 10.4 LTS but I found out that my net-book came with an Atheros pci wifi card, instead of the Broadcom that was advertised on Amazon. 
The first problem was that the wifi switch was hardware locked...I solved this issue thanks to some code I read here, but I am unable to get the Fn+F2 function that enables/disables wifi to work and also the wifi led on the netbook is always off. Anybody has the same issue? Thanks.

---

### Post by varunendra on 2014-01-01
Did you read this thread? - [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

That offers a workaround to the Fn+F2 switch, but unfortunately, there seems to be no fix yet. I'd suggest to file a separate bug report regarding Asus wifi or add yourself as "Affected" to this bug report : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681) (which redirects to the same solution I linked above).

You may track this bug to see when a fix comes out. But I believe it is the confusing title/nature of that report why it has not seen any real fix yet (it originally addressed a particular driver, not Asus notebooks or asus_nb_wmi driver, which is the real culprit). As such, I encourage you to file a separate bug report against "Asus wifi" or "asus_nb_wmi" driver, then comment in the existing bug report and the linked thread above giving us a link to it (so that newly affected users can add themselves to it). If it was not discarded as a duplicate, I hope it will help getting this fixed sooner.

---

### Post by aquanauta on 2014-01-06
> **varunendra said:**
> Did you read this thread? - [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

That offers a workaround to the Fn+F2 switch, but unfortunately, there seems to be no fix yet. I'd suggest to file a separate bug report regarding Asus wifi or add yourself as "Affected" to this bug report : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681) (which redirects to the same solution I linked above).

You may track this bug to see when a fix comes out. But I believe it is the confusing title/nature of that report why it has not seen any real fix yet (it originally addressed a particular driver, not Asus notebooks or asus_nb_wmi driver, which is the real culprit). As such, I encourage you to file a separate bug report against "Asus wifi" or "asus_nb_wmi" driver, then comment in the existing bug report and the linked thread above giving us a link to it (so that newly affected users can add themselves to it). If it was not discarded as a duplicate, I hope it will help getting this fixed sooner.

Yes, I've read that thread.
I know there is a bug report regarding this issue and I add myself to it on Jan 1, 2014.
Are you 100% sure the problem is with the 'asus_nb_wmi' driver?
I got involved in a short email exchange with a Asus technician regarding this problem. This is the transcription of it:

> [FONT=Verdana]Dear Valued Customer,[/FONT]

[FONT=Verdana]Thank you for contacting ASUS Customer Service.[/FONT]
[FONT=Verdana]My name is Kylin and it is my pleasure to help you with your problem.[/FONT]

[FONT=Verdana]We do not have a link to download such a thing, and ubuntu is not a officially support system, we do not have the drivers too, but we have the windows 8 drivers, if you have a windows 8 install disk, you can install the system on it and download the drivers from our website.[/FONT]

[http://support.asus.com/Download.aspx?SLanguage=en&m=1015E&p=3&s=533](http://support.asus.com/Download.aspx?SLanguage=en&m=1015E&p=3&s=533)

[FONT=Verdana]Welcome to refer Troubleshooting & FAQ for ASUS products in ASUS website: [/FONT]
[http://support.asus.com/servicehome.aspx?SLanguage=en](http://support.asus.com/servicehome.aspx?SLanguage=en)

[FONT=Verdana]If you continue to experience issues in the future, please do not hesitate to contact us.[/FONT]

[FONT=Verdana]An email survey will be sent to you within the next 5 days. Please be sure to rate the service I provided to you today.[/FONT]

[FONT=Verdana]Best Regards,[/FONT]
[FONT=Verdana]Kylin_lu[/FONT]
[FONT=Verdana]ASUS Product Support Team[/FONT]
[FONT=Verdana]888-678-3688 [/FONT]

---

### Post by varunendra on 2014-01-06
> **cmayle said:**
> Are you 100% sure the problem is with the 'asus_nb_wmi' driver?

Nope, I'm not 100% sure. But it is certainly not related to any wireless driver and in our attempt to pin-point the problem, the spotlight got stuck on asus_nb_wmi and the 'workaround' is working 100% so far (while still not being able to get the Fn+F2 work). So I am 'Almost 100%' sure it is what we think it is.

It can also be a pm-utils or another power-management feature bug since similar problems have also been reported in HP laptops. But those problems were 'similar', not same, and neither the symptom (working after suspend --> resume) nor the initial workaround of blacklisting the wmi driver (hp_wmi) worked. So that strengthens my belief that it is specific to the asus_nb_wmi driver.

By the way, if I had to rate the response you got from Asus, I'd obviously give it a rating in [COLOR="#FF0000"]minus[/COLOR], not even zero. :/

---

### Post by SeijiSensei on 2014-01-07
Try booting from a 12.04LTS disk, use "Try Ubuntu," and see if the problem persists.  I had some problems with an ath9k adapter around the time I was running 10.10.  A later kernel fixed that problem for me.

If you chose 10.04LTS because you dislike Unity, try Lubuntu 12.04 or Kubuntu 12.04.

---

### Post by aquanauta on 2014-01-07
Thanks Varun. Sorry for my lack of knowledge but, if the problem is with the '[COLOR=#000000]asus_nb_wmi' driver, whose got the obligation to find a solution? Qualcomm, Intel, Asus, etc?
I think it is Asus becuase the product they are sellling should be 100% operational.
[/COLOR]> [COLOR=#000000]Try booting from a 12.04LTS disk, use "Try Ubuntu," and see if the problem persists[/COLOR][COLOR=#000000]
Yes, the problem persists. In fact, I also tried wit saucy salamander and quantal quetzal and the problem is still there. Maybe I'll try Lubuntu. Thanks anyway.
I am still using 12.04 LTS beacuse the machine is still under warranty and is 3 weeks old. ;)[/COLOR]

---

### Post by varunendra on 2014-01-08
This is one of the main problems with FOSS software. Nobody is really 'Obliged' to fix anything. The machine vendor is not because they don't support the OS you are using. The developers are not because they are mostly volunteers and the user didn't pay them for the software.

If you ever read the "[GPL]("http://www.gnu.org/licenses/gpl.html")" licence under which these drivers are released, its "Warranty Disclaimer" clause begins with -
> THERE IS NO WARRANTY FOR THE PROGRAM,....

However, the good part of this kind of licence is that it helps the developers to work without pressure of delivering, and given enough time and information/feedback, they can bring out their best in the software they are working on.

The mass testing/feedback/bug-reporting system is a very important part of this kind of development, to which the users themselves are direct/indirect contributors.

In essence, when you use a FOSS or GPL software, you become part of a system which seeks both freedom and perfection, works really honestly and efficiently to get there, but offers no promises, assumes no warranties or obligations.

What you are using is mostly a work of volunteers, and it WILL become better and better. If you want that to happen faster, consider helping it by contributing whatever way you can. Testing, feedback, bug-reporting, donations, documentation, tech-support, promotions..... even spreading the word to bring in new users can be a contribution in itself.

[FONT=Comic Sans MS]More users = more attention from commercial hardware/software companies = better hardware/software support = better user experience = More users[/FONT]

Hope I didn't go overboard, and you didn't get 'over-bored' :P

---

