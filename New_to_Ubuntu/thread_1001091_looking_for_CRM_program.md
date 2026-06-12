---
title: "looking for CRM program"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by MindyRicker on 2008-12-03
Is there available via OpenSource, a good & reliable CRM program?  What recommendations does anyone have??  Thanks in advance for your recommendations!  

:D Mindy

---

### Post by hyper_ch on 2008-12-03
SugarCRM

---

### Post by grepnix on 2008-12-03
If you want something really powerful I'd recommend SugarCRM. Don't know if its in the repos as I'm not on my ubuntu machine at the moment. I installed it on Pclinuxos using the community edition via the stack installer and it worked like a charm.

I'm sure it'll also be possible on Ubuntu... 

[http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

Regards,
grepnix

---

### Post by uzi09 on 2009-01-20
[VTiger]("http://www.vtiger.com/") is another project that's been brewing up.

I've been looking into migrating to one of these two (SugarCRM & VTiger) from GoldMine, however it looks like it's quite a painful move :(.

If anyone has any details on how to have a successful migration, your help would be greatly appreciated.

(GoldMine 6.5)

---

### Post by clegends on 2009-04-20
Haven't treid Goldmine, but migrated to SugarCRM from ACT2000 a couple years ago. Been anything but painless. It's getting better, but there are some major issues with sugar. The main one is for an open source project, the support sucks. As an open source user I expect to be more on the cutting edge, staying well informed about features... instead, I feel more like a guinea pig set for bait before the big corporations. I had a look at vTiger... but to be honest it didn't seem much better. XRMS looked promising, but seemed a dead project at the time. Since then it's been brought to life again, and might be worth seeing.

Back to Sugar. I still use it, and am about to install it locally, rather than have it hosted on my server (more control, and faster). I'm using 5.0 currently, the most recent one may have added more fixes. Basically, the email was a total joke and waste of time. Until the 5 series the Sugar team used plugins with outlook (perhaps they still do), which is well supported. Now there is an Ajax client which I had high hopes for. Not bad for an integrated mail client on the web, but the campaign settings for group emails were ridiculous. Finally switched to thunderbird, which works beautifully, and has a plugin (there is a plugin, mozilla's not behind it) to integrate with Sugar. Beware however... I had an issue with this plugin, and fried my database.... tend not to use it now....

I still would recommend SugarCRM, just go into it with your eyes open, and ready to look for solutions... it isn't a perfect one. Good luck.

~dinky

---

### Post by t3tech on 2009-04-20
In addition to SugarCRM, there's also OFBiz, Compiere, ERP5, Hipergate. I haven't updated my OSS software page for a while but those are what I have listed for ERP/CRM software packages.

I'm not particularly familiar with any of them though, so I couldn't make any recommendations.

---

### Post by Ubunt2u on 2009-06-23
we're using vtiger and it's ok.  webmail has several persistent bugs that seem to never be fixed.  vtiger team seems to be concentrating more on adding new features rather than stabalizing those already present.  because of this, i hear many complaints from our users.  webmail is very important part of our business, so vtiger's issues in this area may cause us to stop using it before much longer.  only time will tell.  the latest version 5.1 was supposed to be released last november, but is still in beta stages as of now.  that's fine, as long as they get bugs fixed.

---

### Post by CartoonManX on 2009-07-21
You could check out our program. It is a hosting service for vtiger.

[www.aimtheorycrm.com](www.aimtheorycrm.com)

---

### Post by Ubunt2u on 2009-08-11
we just installed vTiger 5.1.  So far seems pretty stable.  The webmail feature is definitely better than before & overall performance is noticeably faster.

---

### Post by Lukas1 on 2009-11-16
I like Sugar, it's a very robust program and there is a good book on it through Packt Publishing by Michael J. R. Whitehead. I haven't tried Vtiger, but there is a ton of backing for Sugar. Like clegends, I also run it locally. I am thinking to put it on my Jaunty server. I'll post how it goes.

---

### Post by timjohn7 on 2009-11-16
At the risk of inviting criticism, have you looked at [www.zoho.com?](www.zoho.com?)  I find ZohoCRM fine for my needs (which are limited).

---

### Post by Lukas1 on 2009-12-31
In response to my last post, I installed SugarCRM on my jaunty server and it seems to work fine except for the email feature, but that's because I didn't configure IMAP, which is necessary. The process was easy enough; after you have LAMP setup right and verified then you download the platform from Sugarforge.com. Then you simply unzip the file, copy the contents to your web folder and change the file permissions. I forget what I set mine to, maybe 757.

---

### Post by dnncrew on 2010-02-22
where can i find beginer level of SugarCRM installation guide adn etc?

---

