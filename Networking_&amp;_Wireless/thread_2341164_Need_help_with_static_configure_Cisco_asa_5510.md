---
title: "Need help with static configure Cisco asa 5510"
date: 2016-10-25
forum: Networking &amp; Wireless
---

### Post by the-phoenix61 on 2016-10-25
Hi all ,

I have buy a cisco asa 5510

Before i do someting i have watch several vidios to understand the working methode of asa 5510
I have find out that the login adres is 10.0.0.2 and that works

Now i have trouble to configure the gateaway in the static route menu with the adsm.
Then i read that the range is not correct and i try to find the erroe but no succes

Example: 

Cable modem -- linksys-dmz -- ip 192.168.1.5 -- gw is 192.168.1.1 -> eth 0/0 asa 5510

Eth 0/1 -- ip 192.168.2.5 -- gw -- 192.168.2.1 -- Pc ping 192.168.2.5 destination host unreacheble

So i want to be connected with both ethernet with static config, i have als fill open dns in the
router and also in the pc.

Is there anyone who have the commands to get the asa working step by step thanx for advice .. 

Ger.

---

### Post by nathan-linux-sa on 2016-10-25
Hi

For starters, I think you are posting this on the wrong forum, but for what its worth it might just be that your Eth 0/1 is shutdown.

I assume you are connected via console to the ASA, if so, login to the console and run the command below:

```

int ethernet 0/1
no shutdown

```

---

### Post by the-phoenix61 on 2016-10-25
I don`t yet have a console cabel yet and i configure the command in the inside promt command
And i gonna do it for all ethernet`s and i let you know if it`s gonna working 

Thx for the info

---

### Post by the-phoenix61 on 2016-10-26
Update i am a lot further now, have install minicom and cnfigure it at 9600 and no flow.
De cables i have ere not network cables but console cables, i ve tested both an all working.
The ethernet cable was also tested via com to rj45 as not working. 

So i am happy after a lot of work and search to get connected, but now i search for ssh remote 
because the firewall is in another room because i want to keep the noise from the cooling ..

Then i go further with adsm and the commandline..

---

