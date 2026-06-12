---
title: "torrent"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by narasimhan1990 on 2008-07-23
hi friends this is my first post here. i am new user of ubuntu linux. 
i want to use torrents in ubuntu. i have a few questions
which is the best torrent manager?
how to install it in ubuntu (i havn't got accustomed with command line)?
how to portforward in ubuntu(i have bridge mode modem)?:confused:
i have not installed any firewall. i just installed the ubuntu live cd. so do i need a firewall?

please answer my queries. 
sorry if this is not the place to post.

---

### Post by ebharv on 2008-07-23
I've never used torrents but I do know that Ubuntu comes with a torrent manager called Transmission. It should be under the Internet section of the Applications menu (Applications->Internet->Transmission). Or you could do Alt+F2 type "transmission" (no quotes) or from a terminal "transmission" (no quotes).

I don't know how good Transmission is though, like I said before I've NEVER used torrents, but maybe it'll hold you over 'til you find something better.

---

### Post by Yuki_Nagato on 2008-07-23
Deluge works for me.  Transmission did not work well for me.

```
sudo apt-get install deluge-torrent
```

That will install it for you if entered into the command line.

---

### Post by narasimhan1990 on 2008-07-24
thanks i'll try transmission and reply. but what about my other questions?

---

### Post by vishzilla on 2008-07-24
if you want a utorrent experience I would suggest Deluge or for simpler interface Transmission is best. iptables is the firewall installed by default but allows all traffic. To control the iptables, Uncomplicated Firewall (ufw) is installed in 8.04. You can enable it by entering in the terminal [Application>Accessories>Terminal] ```
sudo ufw enable
``` you can read the manual to set the rules ```
man ufw
```

---

### Post by narasimhan1990 on 2008-07-24
i have basic ubuntu version(just installed from live cd) so there is no transmission. i'll download and try deluge

---

### Post by superprash2003 on 2008-07-24
if you are using bridged mode then all traffic comes to your computer.. ubuntu has built in iptables which is a powerful firewall..if your torrent is listening to a certain port, then iptables would automatically allow any traffic through that port, and would block all other ports.. you could also use utorrent with WINE if you are comfortable with utorrent

---

### Post by ebharv on 2008-07-24
The installation question I can handle. There are two ways to install programs graphically with Ubuntu. The first is Applications->Add/Remove. Type in what you are looking for in the search box or browse through the categories. Just make sure that the "Show: " selector is on "All available applications" or you may not find anything.

The second method is through System->Administration->Synaptic Package Manager. This is probablly the way most non-apt-getters go. There's a search button for finding packages (programs). Just click-type-find. Word of caution though, in Synaptic the list that is shown contians the name of the actual .deb file which is the package. This may or may not be the name of the actual program you are using, so make sure you read the descriptions.

You can only run one or the other not both, and they both ask for the admin password. One more thing, to maximize your hits when searching for packages (for either method) make sure the universe and mulitverse repositories are active. It can be done through System->Administration->Software Sources. Click the first tab and check the repositories you want. You can add repositories in the "Third-Party Software" tab. This app is also available through a button (or menu item) in Synaptic.

That's all I got.

---

### Post by ebharv on 2008-07-24
The installation question I can handle. There are two ways to install programs graphically with Ubuntu. The first is Applications->Add/Remove. Type in what you are looking for in the search box or browse through the categories. Just make sure that the "Show: " selector is on "All available applications" or you may not find anything.

The second method is through System->Administration->Synaptic Package Manager. This is probablly the way most non-apt-getters go. There's a search button for finding packages (programs). Just click-type-find. Word of caution though, in Synaptic the list that is shown contians the name of the actual .deb file which is the package. This may or may not be the name of the actual program you are using, so make sure you read the descriptions.

You can only run one or the other not both, and they both ask for the admin password. One more thing, to maximize your hits when searching for packages (for either method) make sure the universe and mulitverse repositories are active. It can be done through System->Administration->Software Sources. Click the first tab and check the repositories you want. You can add repositories in the "Third-Party Software" tab. This app is also available through a button (or menu item) in Synaptic.

That's all I got.



**[SIZE="4"]CAN SOMEONE REMOVE THIS ACCIDENTAL DOUBLE POST.[/SIZE]**

---

### Post by narasimhan1990 on 2008-07-24
thanks dude its working

---

### Post by diwas on 2008-07-24
I was havin hell lot of problem with Azureus. Then i came across this post and installed deluge...and it works great. Thank you.

BTW y does azureus has to be so complicated????

---

### Post by narasimhan1990 on 2008-07-24
now a part of the problem is over. now i need to know certain things
how to schedule the command "pon dsl-provider" to run in terminal at 2:05 am by waking up the computer from suspend mode? (this is the command to start internet connection)

how to schedule deluge to start at 2:10am because i can't sacrifice my sleep everyday?(i have night 2-8 free unlimited)

guys please reply.
superprash if u know please reply.

---

### Post by diwas on 2008-07-24
Yeah i wud like to know that too....but wat if something goes wrong wid pon dsl-provider???(i mean some error stuff)
 hehe computer wud be just on for nthg!! haha.

---

### Post by narasimhan1990 on 2008-07-24
yeah that happens to me always. that means we also need to know how schedule to schedule the command "pon dsl-provider" everytime the computer automatically disconnects?

---

### Post by narasimhan1990 on 2008-07-25
why no answer to my questions

how to schedule the command "pon dsl-provider" to run in terminal at 2:05 am by waking up the computer from suspend mode? (this is the command to start internet connection)

how to schedule deluge to start at 2:10am because i can't sacrifice my sleep everyday?(i have night 2-8 free unlimited)

i also need to know how schedule to schedule the command "pon dsl-provider" everytime the computer automatically disconnects?
guys please reply.

---

### Post by narasimhan1990 on 2008-07-25
i've found out the way to schedule. in applications->add/remove enter schedule in search bar( with all available applications).
there will be schedule install it.
then u can open schedular from applications->system tools->schedule

but u need to keep Ubuntu active for scheduler to work(it doesn't work in suspend mode). so your only option to save power is to off your monitor.

guys if u could find a scheduler to wake up Ubuntu from suspend mode please inform. thanks superprash for providing me this info.

---

### Post by diwas on 2008-07-25
There cud be someway...it is linux man...heheh!! jk.

---

### Post by evets25 on 2008-07-25
I use ktorrent, (even though it's a KDE app and I use gnome) and it comes with a bandwidth scheduler plugin that lets you control when it starts up and stops and stuff. It's quite useful, and I also love the interface, which I find very similar to utorrent, but with more features. You should check it out.

---

### Post by narasimhan1990 on 2008-07-26
deluge is great (it downloads with full speed without crashing).
but i haven't yet figured out how to save power?

---

### Post by freakalad on 2008-07-30
I use torrentflux (b4rt variety) to run a web-based torrent client/server on a little machine with an ext hdd. 
that way i can post downloads jobs to the server from any of may machines on my network, or remotely, and download it over the lan when complete. even has a firefox add-in :)

my solution works pretty good (too good), but is still not perfect, as I have trouble starting & stopping the service automatically. 

i now need to ensure that i can schedule downloads from 00:05 to 07:55. there's a fluxcli.php file that's supposed to start & stop the service, that i've tried scheduling via cron & crontab (that's how you guys can schedule jobs, btw), but there seems to be a misconfiguration somewhere. the job will start but not stop. and it only seems to stop downloading, and not uploading
i've also tried applying access restrictions to my linksys routers, but no dice.

my next step would be to cron some iptable commands, to route the torrent data to loopbacks @ off-time.

can anyone give me some advice what these commands should look like. i think i can limit the ports to 49000-50000. i'd like to add these cron jobs to both my ubuntu web/download server, as well as my ipcop firewall, to make double sure that nothing gets through?
ps. how can have the iptables in a correct state it the machine was down during missed event? maybe cron copy/remove a script into cron.hourly?

---

### Post by DisasterEC on 2009-06-12
> **freakalad said:**
> I use torrentflux (b4rt variety) to run a web-based torrent client/server on a little machine with an ext hdd. 
that way i can post downloads jobs to the server from any of may machines on my network, or remotely, and download it over the lan when complete. even has a firefox add-in :)

my solution works pretty good (too good), but is still not perfect, as I have trouble starting & stopping the service automatically. 

i now need to ensure that i can schedule downloads from 00:05 to 07:55. there's a fluxcli.php file that's supposed to start & stop the service, that i've tried scheduling via cron & crontab (that's how you guys can schedule jobs, btw), but there seems to be a misconfiguration somewhere. the job will start but not stop. and it only seems to stop downloading, and not uploading
i've also tried applying access restrictions to my linksys routers, but no dice.

my next step would be to cron some iptable commands, to route the torrent data to loopbacks @ off-time.

can anyone give me some advice what these commands should look like. i think i can limit the ports to 49000-50000. i'd like to add these cron jobs to both my ubuntu web/download server, as well as my ipcop firewall, to make double sure that nothing gets through?
ps. how can have the iptables in a correct state it the machine was down during missed event? maybe cron copy/remove a script into cron.hourly?

Hi did you work out a way to start and stop torrentflux ? I have been trying to work out the same thing need start it at 12am and stop it at 7am.

---

