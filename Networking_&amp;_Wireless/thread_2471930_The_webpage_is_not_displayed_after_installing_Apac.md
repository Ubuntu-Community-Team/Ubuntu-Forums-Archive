---
title: "The webpage is not displayed after installing Apache2"
date: 2022-02-13
forum: Networking &amp; Wireless
---

### Post by bart81818 on 2022-02-13
Hello,

I have a problem with viewing the default site (localhost/127.0.0.1) on my browsser after installing apache2.


1) Service is up and works fine:

&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: active (running) since Sun 2022-02-13 17:02:12 UTC; 2min 25s ago
  Process: 590 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
 Main PID: 744 (apache2)
    Tasks: 55 (limit: 1105)
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;744 /usr/sbin/apache2 -k start
           &#9500;&#9472;745 /usr/sbin/apache2 -k start
           &#9492;&#9472;746 /usr/sbin/apache2 -k start


Feb 13 17:02:05 nevada systemd[1]: Starting The Apache HTTP Server...
Feb 13 17:02:12 nevada systemd[1]: Started The Apache HTTP Server.

2) But on the browser (chrome/inernet explorer) there is no way to view the page:

This site cannot be reached 
Server 127.0.0.1 has rejected activity.


Do you have any ideas what is wrong? I checked also security on my PC and it doesn't block the server.

Thank you in advance for any help,

Bart

---

### Post by TheFu on 2022-02-13
Is apache running on the same computer as the browser?
Is the firewall enabled and allowing http/https traffic?
Some browsers automatically convert 80/tcp ---> 443/tcp ... i.e. they insist that you should be using https.

Can you share the apache config file you think is being used?  What is the virtualhost setting?

---

### Post by bart81818 on 2022-02-14
[COLOR=#000000]Is apache running on the same computer as the browser? 
[/COLOR]Yes,  it does. Virtualbox is installed on my PC, I set one virtual machine on my PC and then installed apache on it.
[COLOR=#000000]Is the firewall enabled and allowing http/https traffic?
[/COLOR]On my Ubuntu:
root@nevada:/etc/apache2# sudo ufw status
Status: inactive

On Windows:
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAacAAAAZCAYAAACVWOEpAAAEuklEQVR4nO3dvY7iSBSG4XdWew8eO9/UCPseEEIONtgctUTsGIlgNAESccWWWo432MRCLd8DIBzuBWB8FbMBf24a9/DTLNWj78kaivIpq1XHPlSZL3//8  Pv/78g8 nIp MyVa7v0MGpo//yJBuUpDGU9zRkI7z6Fg o486f7/a/5XI5/Tl8yYnERH5Vf326ABERESOKTmJiIh1lJxERMQ6Sk4iImIdJScREbHO7 c0 v79 9kdfvv27epgRETk/2Xr/H5WcoLzgjoeZJHGTN0Rw/rGkyIlXrQx3TWT8Zzgbvt66vteCtI4YVZ7NxwY jduXrFnfMevJ8zCAebEAKt8wjiD6Kq43tlLVOV3Hq I3Ms18/u9fUhZ70tD0H47ZFVWr14rFjPCtg9Oh6FpmsgK0nhCXp1671oe0chgjMGMIsokpbixR7vGV fhldMT/Re8HHaXfqx3xysin1XT/H5vNyendwN3XLzZopYEChazkPajt9s7X3EpWd aHGwdH C6MF8eDbBYMAtDwseEJCKfzKMSE1xQ1oNNoD9qt38/DdxpEXgZi6KP77OdHNv0gbdltymEMJvVruzHMVk4wPQ5Kie9Li8VaUyyq9k1lLNeKRbMwh5md5Vf5UzGGbsjb0p m8fYzINt2a5Iiacuo2GH/c2BreMD3G4Pxi8Und2jdyryaUn01KOclYdT0dj368f4vCqD1s6XF 3Kmm/H60YuWbbp/NDu Hzr8UAiNrh4fr zi5ITHAZQD/xHY73SoRV4zNcV M625NVvaLuidEcYczzRAT8pwPl9g mz/1ze9U Ul1Zk45gM2EyIu mwIB1nuAPD0Gc7cU7IR0M6wwFl/ELRabNIYGBqicm68b35FO0wOSTOasmcgCcHynqrk30fErMZHh9oRTYNGBmDU6TEST0BHrUrexjT3yT2fbuCdDwnGBmGDlCkTPIKX/VAkYe7bH6/r4uTE3BR4E4rgOclVafFuvRwu00tPYLWlRNUkRLvL/89oob 94sAqpxJPGE9GtJhTUlIbze7Oh16YcaiAhyf/mBBHCeEA3Py6t6e8b3ldyOmzzmV36F6yXB7Buc4EZ7qu1oyX4X03iSmbZunbZL224RM2ebmt 262zNWb8eakhWz/YUCELYBJScRG9iQmODC5HRVRnVaBDyzLNhfuX oKmeSwMAYfCryyfN5MXkZZcXtc6KN4zsVWxnxdHxTd0vfN1EpT8Q2ttwx7Vy8IGIX8PmBO7QCyJIMgtaVucDB9VbsF8YVi8Oy8Kpk5bmbfqsl83MWo1VL5isP12G7OGLGYndDUeVM94saCtIEBmYAjav7LBxfrd9Oz22Oralvp0XgzZjeYznh9nzfpW8Rucnl8/v9XFXWuzRwpxXgZVxQ1tp8X5LsFwz4dHohcRJvJu36ijO/SzQdM44z8EJCr6nP ndOtRIfPv1RxGQcE9fe29xJJJTRiD4OTjRlPMlfL4iwanxNh oSefD11Hc6jX072 /bxsTb2ttH7AvbHnR7vg99n7vIQ0Tuz4bEBGf npOtO4hFROQ2ts7v rFBERGxjh78KiIi1lFyEhER6yg5iYiIdZScRETEOkpOIiJiHSUnERGxzn8qTbeajFwSNgAAAABJRU5ErkJggg==[/IMG]
In the firewall option I allowed connection for Virtualbox
[COLOR=#000000]Some browsers automatically convert 80/tcp ---> 443/tcp ... i.e. they insist that you should be using https.

[/COLOR]I manually taped http:// to avoid this situation

[COLOR=#000000]Can you share the apache config file you think is being used? What is the virtualhost setting?

[/COLOR]I add the notepad with the output from file

Thank you for your reply

---

### Post by TheFu on 2022-02-14
Whoa there ... way to bury the lead!!!!

A VM is **not** the same computer.  It is a VM.  VMs support lots of different network connection methods. Depending on which network type you've setup for the VM, the connectivity may be a minor issue or could be impossible.  Assume a VM is a completely different computer. It is.  That's sorta the point.  VMs get a different network address, so [http://localhost/](http://localhost/) on the physical computer won't access any VM running under it.  Also, some browsers will ignore http:// URLs and insist on HTTPS:// - always.

I recommend you read up on the virtualbox online manual for the different types of networking supported. Google finds it easily ... I think it is in chapter 6.

---

### Post by bart81818 on 2022-02-16
Ok thanks a lot TheFu, now i get it. After your comment I installed virual desktop and there it works, for now I need it just for a test. I am going to study this 6th chapter to understand what's wrong with my connection.

---

### Post by TheFu on 2022-02-16
> **bart81818 said:**
> Ok thanks a lot TheFu, now i get it. After your comment I installed virual desktop and there it works, for now I need it just for a test. I am going to study this 6th chapter to understand what's wrong with my connection.

If you want the VM to be located on the same subnet as the host system, the easy answer is to use "bridged" networking. That is a single checkbox.  Also, be certain that you setup the "server" with a static IP. Don't use DHCP.

If your network-fu is weak, you'll need to learn some of that before anything makes sense.  Episode 25 of "Security Now!" podcast begins with "how the internet works."  This is a primer for how all IPv4 networking works. I think it has 3 parts. Even if you have an idea, it is worth your time to read/listen to those podcasts to solidify that knowledge.  Leo and Steve do talk way to much about non-related stuff. 

I think some other people have gone through all those podcasts to remove the junk, so a 90 minute podcast is condensed to the 30 minutes we care about. Bet google will find their versions. I haven't listened in years. Got tired of the coffee/vitamin d and other non-sequitur junk. They drove me away.  Plus, a single episode was longer than my commute.

---

