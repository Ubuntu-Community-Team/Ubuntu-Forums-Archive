---
title: "get the random ip"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by piteur on 2008-07-26
Hi guys,
i need some help, pleze.. Last year Phillips321 posted this message:

-----------------------
hi guys,

i have a headless box that sits on a dhcp network.

each time the machine boots it sometimes changes it's IP, there is no way i can use a static ip as it's on the company network. how do i go about sending myself the ip each time the box boots?

email? what other message options do i have?

cheers
-----------------------

I have the same problem, but i would be able to get my pc in the office from a remote location via ssh. I have no problem to configure the router, my only problem is the non static ip.

Is there a way to configure my ubuntu box in the office to send every 30min an email with it's public ip (maybe with a small php script)?

Sorry for the stupid question (i'm a newbie) and for the bad english (i'm italian). XD

Thanks.

---

### Post by kevdog on 2008-07-26
Why don't you use noip or dyndns that would update your computer's IP address with a name you have associated with your computer.  That way you would only have to connect via name and not ip address.  Both services have dynamic updater clients so its easy your computer's IP address is updated (I think the minimum is every 5 minutes).

---

### Post by treymul on 2008-07-26
I ran into the same thing with my home desktop.  My ip changes fairly regularly, so I wrote a script that checks the ip and emails it to my web email so that I always know what my home ip is.

touch ~/temp/ipaddress
wget -O ~/temp/ipaddress [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp)

cd /home/username/temp
gpg -r username -e ipaddress

sendEmail -s smtp.gmail.com:587 -xu username -xp password -o tls=yes -f emailaddress -t emailaddress -u "ip address" -m "new ip address" -a /home/username/temp/ipaddress.gpg

cd /home/username/temp/
rm ipaddress.gpg

the wget line checks ip address and saves it in file named ipaddress, I then encrypt and mail it to my self.  I put this is crontab to run everyday, so that if I can't ssh to my computer, I can get the new ip from my email.  Its not as neat as the early suggestion, but it works for me.

---

