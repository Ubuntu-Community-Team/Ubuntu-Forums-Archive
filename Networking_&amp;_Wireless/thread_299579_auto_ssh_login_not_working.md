---
title: "auto ssh login not working"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by rhodry on 2006-11-14
I am having a real nightmare getting automated login with ssh to work; hoping someone can guide me. I am running Edgy.

I have a main machine (called greywolf) which has a partition for my /home on it. I am doing backups to an extrnal usb drive attached to a Linksys NSLU2 (called slug) running UnSlung firmware. All hosts, networking, shares, firewall & such stuff is working fine. Currently I use this command on greywolf to push-backup some key files to the external drive:

rsync -avz --delete --numeric-ids /home/paul/somefiles -e ssh paul@slug:/backup/edgy

I get asked for paul´s password on slug and away it goes. Works like a charm creating ´somefiles´ on slug. I want to automate this process through cron so, I worked out I have to get ssh working automatically and without password. I gathered a few howtos etc from around the web and settled on the commands below to set it up:

on greywolf - $ssh-keygen -t dsa ; put the file in /home/paul/.ssh, answered passphrase with <enter> only.

then I copied the .pub key to slug, appending it to user paul´s authorized_keys file. I used the command:

$cat ~/.ssh/id_dsa.pub | ssh paul@slug ¨cat- >> ~/.ssh/authorized_keys¨

Now, interestingly, I did this in reverse as well. i.e. I opened a session on slug with Putty and generated the keys and sent them to my home on greywolf. I mention this because here is my problem and dilema?!

If I start on slug (in a Putty ssh session) I can type $ssh paul@greywolf and it works just fine, no passwords, just a command prompt on greywolf. Just what I expect.

However, it does not work the other way, which is what I want for the backups to be automated. If I type ssh paul@slug from command prompt on greywolf, it insists on still asking for paul´s password on slug before making the connection. I am quite perplexed as to why it works in one direction and not the other.

I was wondering whether I should try rsa keys instead, but this way works from slug to greywolf?

I have even done a diff on the ssh_config and sshd_config files from each location and I cannot see an obvious problem to cause this. I would appreciate advice on further tests I might conduct to debug this or a solution even?! :)

---

