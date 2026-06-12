---
title: "DSL stopped working"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by DKCO on 2007-02-27
Hi all, here's me situation in brief -

-I did a clean install of Ubuntu Edgy.
-I successfully set up my dsl connection by using ppoeconf in the terminal and clicking enter a few times.  It was set to connect at startup which it was doing without problems.
-Ubuntu alerted me of security updates, which I downloaded.
-I installed Automatix2 to get some essential files.

So here's my problem - I restarted my computer and went to connect Automatix to the internet for the first time and couldn't connect.  Under Administration>Networking it said eth0 was enabled and using DHCP.  I tested my ISP with Windows and it worked fine, so the problem is something in Ubuntu.  I then:

-Tried 'pon dsl-provider' in the console.  It told me "plugin rp-pppoe.so loaded", but I still got nothing.  
-I then tried 'poff' in the console, and it told me, "more than one ppd running and no -a option and no arguments supplied.  Nothing stopped".  I then tried to bring up the connection again, and still... nothing.
-I then uninstalled Automatix2, trying to retrace my steps.  This did nothing.

So I searched the forums for a similar problem and couldn't find anything.  I also Googled the error it gave me ( about 'no -a option' ) and found nothing. 

Any ideas as to what this could be?  Oh, and my Ubuntu experience is almost null, so I can answer any questions as best I can, but don't expect too much!

Thanks,

David

---

### Post by DKCO on 2007-02-27
Huh... well it's working now, so nevermind, I guess.  I just restarted, and tried the 'poff' and 'pon dsl-provider' commands again, though this time the 'poff' command gave me something different.  So I imagine it had something to do with that initial error, "more than one ppd running and no -a option and no arguments supplied.  Nothing stopped".  I guess I don't need any more help at this point, but if someone can explain what that meant, I'd appreciate it.

David

---

### Post by Sainarx on 2007-02-27
> **DKCO said:**
> Hi all, here's me situation in brief -

-I did a clean install of Ubuntu Edgy.
-I successfully set up my dsl connection by using ppoeconf in the terminal and clicking enter a few times.  It was set to connect at startup which it was doing without problems.
-Ubuntu alerted me of security updates, which I downloaded.
-I installed Automatix2 to get some essential files.

So here's my problem - I restarted my computer and went to connect Automatix to the internet for the first time and couldn't connect.  Under Administration>Networking it said eth0 was enabled and using DHCP.  I tested my ISP with Windows and it worked fine, so the problem is something in Ubuntu.  I then:

-Tried 'pon dsl-provider' in the console.  It told me "plugin rp-pppoe.so loaded", but I still got nothing.  
-I then tried 'poff' in the console, and it told me, "more than one ppd running and no -a option and no arguments supplied.  Nothing stopped".  I then tried to bring up the connection again, and still... nothing.
-I then uninstalled Automatix2, trying to retrace my steps.  This did nothing.

So I searched the forums for a similar problem and couldn't find anything.  I also Googled the error it gave me ( about 'no -a option' ) and found nothing. 

Any ideas as to what this could be?  Oh, and my Ubuntu experience is almost null, so I can answer any questions as best I can, but don't expect too much!

Thanks,

David
I have exactly the same problem! But it don`t work for me even when I restart it 5-6 times! Please help! :(

---

### Post by zvacet on 2007-02-27
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

---

### Post by Sainarx on 2007-02-27
> **zvacet said:**
> [http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")
Still not working.... :sad:

---

