---
title: "Say your word, What is your best VOIP program?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by juliobahar on 2010-01-18
Dear All,

After totally shifting to ubuntu (bye bye Micro$oft), I only look back for two things:

[LIST]
[*]1- Games ... yet not missing them so much as I guess I'm growing older for games and recently my skills have dramatically deteriorated.

[*]2- a VOIP program called **SMSlisto**, that I truly miss, I used for all my international calls and even local landline calls for the reason that they are FREE.
[/LIST]

I've tried setting up Ekiga to connect to my SMSlisto and other VOIP accounts that I have, Alas! Ekiga doesn't seem to be a stable program yet, with audio & connection issues as well.

I also tried running the SMSlisto prog from a windows guest on a virtualbox, but after upgrading to Karmic the sound isn't consistent. 

If you use VOIPs, from your point of view, what is the best VOIP so far to run on UBUNTU?

---

### Post by Arla on 2010-01-18
Skype does seem to work, although I wish I could find something else that worked well between Windows and Ubuntu.

---

### Post by juliobahar on 2010-01-18
> **Arla said:**
> Skype does seem to work, although I wish I could find something else that worked well between Windows and Ubuntu.

Yes I guess Skype is more dedicated to linux than others. But the rates aren't cheap. Honestly I haven't gone deeply into the world of skype under linux.

---

### Post by s.fox on 2010-01-18
Hello,

I only really use Skype myself for VOIP,  but found [this]("https://help.ubuntu.com/community/VoIP") page in the community wiki that might be of some interest to you.

-Silver Fox

---

### Post by medley on 2010-01-18
I use Zoiper as a SIP client. It is available for both Windows and Linux.I also have my own, dedicated VoIP server at my house. I use the PBX-In-A-Flash distribution for this. This is my home's exclusive telephone provider (ie, Me), and has been for the last 2.5 years.

I don't know if the service you are accustomed to requires its own software client. If they can accept generic SIP connections, Zoiper Free is a good option.

Cheers

---

### Post by Captain_tux on 2010-01-18
Skype has given Linux a lot of attention and I'm grateful for that... but I still can't send SMS with Skype from Linux.

---

### Post by juliobahar on 2010-01-19
> **medley said:**
> I use Zoiper as a SIP client. It is available for both Windows and Linux.I also have my own, dedicated VoIP server at my house. I use the PBX-In-A-Flash distribution for this. This is my home's exclusive telephone provider (ie, Me), and has been for the last 2.5 years.

I don't know if the service you are accustomed to requires its own software client. If they can accept generic SIP connections, Zoiper Free is a good option.

Cheers

This looks tempting have to give it a try.

What about Gizmo has anyone tried it for a feedback to the community?

Regards

---

### Post by juliobahar on 2010-01-25
Zoiper is really good, it did the job for me in contrast to Ekiga. I'm able to use my sip account with the zoiper communicator program. Audio was flawless. Haven't tried the video.

One question. if I where to signup for a Zoiper account. How can I top it up with credit? Honestly I searched everywhere, couldn't find a thing.

---

### Post by medley on 2010-01-25
> **juliobahar said:**
> Zoiper is really good, it did the job for me in contrast to Ekiga. I'm able to use my sip account with the zoiper communicator program. Audio was flawless. Haven't tried the video.

One question. if I where to signup for a Zoiper account. How can I top it up with credit? Honestly I searched everywhere, couldn't find a thing.

I don't know if Zoiper provides their own telephony service or not. You can search your own service provider just by googling "telephony service providers". There are many, many of these with their own pricing structures (ie, pay as you go, monthly flat rate, etc). Find one that allows you to set up your own trunk with them, and direct your Zoiper client to the account you set up. I'm in Canada and use two located here, but the TSP doesn't have to be in your home country. It is with them that you would apply credit to your account. [www.voip-info.org](www.voip-info.org) is a good source of information, including service providers.

Good luck.

---

### Post by michaelbr on 2010-08-12
Greetings all:
I'm new to Linux/Ubuntu (I've tried several times previously using Redhat and Ubuntu, but only occasionally, now I'm trying harder with Lucid), so please bear with me, I'm a newbie (being always a Wind/M$ user, but not fond of them).

> **juliobahar said:**
> Yes I guess Skype is more dedicated to linux than others. But the rates aren't cheap. Honestly I haven't gone deeply into the world of skype under linux.

juliobahar: can you please tell me 
1) which service provider are you using (if this info is not confidential)? Currently I'm using Mediaring, but their quality is not very good (I can hear them fine, but they can't hear me well, they said the volume is very low, but I've setup the volume to max!!!)
2) how did you install Zoiper (I've learned how to install packages through Synaptic Package Manager (I didn't find Zoiper there) and Ubuntu Software Center (didn't find it there either), so I'm assuming you have to download it and install it. Could you please let me know step by step how to install it?

medley:
sorry for this dumb question. What's the advantage in having your own VoIP server? If I'm interested in setting it up, can you point me how/where to start?

---

### Post by ubudog on 2010-08-12
I use Skype.  It works pretty good on Ubuntu.

---

### Post by juliobahar on 2010-08-13
> **michaelbr said:**
> 

juliobahar: can you please tell me 
1) which service provider are you using (if this info is not confidential)? Currently I'm using Mediaring, but their quality is not very good (I can hear them fine, but they can't hear me well, they said the volume is very low, but I've setup the volume to max!!!)
2) how did you install Zoiper (I've learned how to install packages through Synaptic Package Manager (I didn't find Zoiper there) and Ubuntu Software Center (didn't find it there either), so I'm assuming you have to download it and install it. Could you please let me know step by step how to install it?



Ho ho ho, quite a long message for me to reply, as I'm being a little lazy today. Anyway here it goes and you are welcomed anytime to ask questions I hope I can reply:D

(1) well I do use Betamax voip services which really are plenty and ones that I've used and still are - for instance - smslisto, voipcheap, justvoip, rynga ... etc. 
the problem is that they  come with a windows only software. And to use them I have to run a window virtual box and do my calls, which can be inconvenient at times. 

I have no experience with Mediaring, sorry.

I've contacted Betamax constumer service previously they seemed reluctant to support Linux at the moment. They stated that I can use Linphone (which I detested for being unstable, difficult to setup and the line wasn't stable) then I started searching for others but to no avail.

Btw Lucid come shipped with empathy that can support voip, why not trying that and giving us a feedback. personally I have set it up but never remembered to use it for practically calling someone.

others on ubuntuforum have advice us to use sofia phone - honest I haven't till this date.

(2) thanks for reminding me with Zoiper. I used it long time ago and stopped because it stopped running all suddenly with a strange bug that I can't remember at the moment.

Anyway to install Zoiper go to

[http://www.zoiper.com/download_list.php]("http://www.zoiper.com/download_list.php")

Go down in the page, find your ubuntu specific installation, download the file just by double clicking it, ubuntu package manager with start downloading the file after prompting for you superuser password.I guess you should use karmic if you have Lucid. Lucid package isn't available yet at their website.

I hope I was able to answer your questions.No questions are stupid, but answers can be!!!

---

### Post by TNT1 on 2010-08-13
We sell enterprise VOIP solutions at work, and internally we use Ekiga or Linphone for the linux users.

---

### Post by michaelbr on 2010-08-13
> **juliobahar said:**
> Ho ho ho, quite a long message for me to reply, as I'm being a little lazy today. Anyway here it goes and you are welcomed anytime to ask questions I hope I can reply:D

(1) well I do use Betamax voip services which really are plenty and ones that I've used and still are - for instance - smslisto, voipcheap, justvoip, rynga ... etc. 
the problem is that they  come with a windows only software. And to use them I have to run a window virtual box and do my calls, which can be inconvenient at times. 

I have no experience with Mediaring, sorry.

I've contacted Betamax constumer service previously they seemed reluctant to support Linux at the moment. They stated that I can use Linphone (which I detested for being unstable, difficult to setup and the line wasn't stable) then I started searching for others but to no avail.

Btw Lucid come shipped with empathy that can support voip, why not trying that and giving us a feedback. personally I have set it up but never remembered to use it for practically calling someone.

others on ubuntuforum have advice us to use sofia phone - honest I haven't till this date.

(2) thanks for reminding me with Zoiper. I used it long time ago and stopped because it stopped running all suddenly with a strange bug that I can't remember at the moment.

Anyway to install Zoiper go to

[http://www.zoiper.com/download_list.php]("http://www.zoiper.com/download_list.php")

Go down in the page, find your ubuntu specific installation, download the file just by double clicking it, ubuntu package manager with start downloading the file after prompting for you superuser password.I guess you should use karmic if you have Lucid. Lucid package isn't available yet at their website.

I hope I was able to answer your questions.No questions are stupid, but answers can be!!!

juliobahar: thanks for your prompt and detailed reply. I used previously Betamax too, but in the last 2 years, I've been having payment problem (lack of credit card payment option for China) and unable to connect, I'm not sure if this is only local problem (China) or not. Have you ever had connection problem with them? I tried to send email to them, and they never replied. Do you know if any of those Betamax clones have SIP settings (it seems to me that you need it to setup the apps in Ubuntu).

---

### Post by Blutkoete on 2010-08-13
For the games part: Maybe you'd like to try out Battle for Wesnoth, it's in the repositories, and it's a nice turn-based strategy game with difficulty levels from very easy to annoyingly hard.

I like the turn-based part because you can play the game at the speed you prefer (as opposed to modern real-time strategy games).

---

