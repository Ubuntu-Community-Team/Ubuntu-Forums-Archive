---
title: "Whats the deal with Mediabuntu???"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by PPPilot on 2010-04-20
I have a package or three installed from the Mediabuntu repos. I am running Karmic and have been out of town for a few days. Today when I started my computer it ran the Update Manager and the update failed due to a time out on Mediabuntu. Then I ran ```
sudo aptitude update && sudo aptitude safe-upgrade
``` from the terminal and got these errors:

```
Err [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic Release.gpg                            
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/free Translation-en_US                
  Unable to connect to packages.medibuntu.org http:
Err [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/non-free Translation-en_US            
  Unable to connect to packages.medibuntu.org http:

``` Are they down or what. Seems like since this error is failing the whole update process since the process never finishes. Any Ideas???

---

### Post by Didius Falco on 2010-04-20
Read this for answers/solutions:

[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

Regards,

Didius

---

### Post by refitman on 2010-04-20
Thanks for the link, that's sorted it right out.

---

### Post by Didius Falco on 2010-04-20
My pleasure!!

---

### Post by wilee-nilee on 2010-04-20
> **Didius Falco said:**
> Read this for answers/solutions:

[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

Regards,

Didius

Good job, you are my new hero. ;)

---

### Post by tripolitan on 2010-04-20
Thanks!

---

### Post by alexcckll on 2010-04-20
I personally dfon;'t understand.  When is Canonical going to fix this? All I know is the systems update are broken.

---

### Post by Didius Falco on 2010-04-20
> **alexcckll said:**
> I personally dfon;'t understand.  When is Canonical going to fix this? All I know is the systems update are broken.

It's not Canonical - Medibuntu is a 3rd party repository and Canonical have nothing to do with it.

To fix your updates, you can:

1. Follow the link I posted and try out the three mirrors for Medibuntu until you find one that works for you.

2. Open up Software Sources (**System/Administration/Software Sources**) and uncheck the Medibuntu repo under the **Other Software** tab and then allow it to reread the sources, then update as usual.

3. Wait until Medibuntu comes back online - last reports is that they expect to be back some time on Thursday, on the US side of the International Date Line, and then update as usual.

Unless you've got some show-stopper bug, I'd just wait a day to update.

---

### Post by mick222 on 2010-04-20
Unless your just installing Ubuntu or upgrading is there any need to use the medibuntu repos.I normally uncheck them after i install the w32codecs and libdvdcss

---

### Post by Didius Falco on 2010-04-20
> **mick222 said:**
> Unless your just installing Ubuntu or upgrading is there any need to use the medibuntu repos.I normally uncheck them after i install the w32codecs and libdvdcss

You generally won't pull down much, if anything,  from them, so I just leave well enough alone. There are the occasional updates to the codecs, etc., but for the most part, you are right.

---

### Post by zander1013 on 2010-04-20
i am not having luck with [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

the result is always similar despite the hit.

shouldn't the mirrors go dark if the source of the image is unavailable?

---

### Post by mick222 on 2010-04-20
> **Didius Falco said:**
> You generally won't pull down much, if anything,  from them, so I just leave well enough alone. There are the occasional updates to the codecs, etc., but for the most part, you are right.

Thx i just realised i haven't installed libdvdcss on lucid I very rarely play dvd's on this computer . Maybe i should have enabled it .

---

### Post by polly1 on 2010-04-21
Hi  
 
This may be helpful

Please see this thread [http://ubuntuforums.org/showthread.php?t=1458747](http://ubuntuforums.org/showthread.php?t=1458747)

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

---

