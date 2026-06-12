---
title: "alias and avg 8.5"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-04-26
i have tried 

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias home='cd /home/lance'
alias documents='cd /home/lance/Documents'
alias downloads='cd /home/lance/downloads'
alias openline='cd /home/lance/MyDownloads'
alias shared='cd /home/lance/Shared'
alias whereami=pwd
alias whereareyou=pwd
alias where=pwd
alias whoareyou=whoami
alias full=´avgscan -H /home/lance´
alias update2=´sudo avgupdate -p 2´

and

alias update=¨sudo apt-get update¨
alias upgrade=¨sudo apt-get upgrade¨
alias home=¨cd /home/lance¨
alias documents=¨cd /home/lance/Documents¨
alias downloads=¨cd /home/lance/downloads¨
alias openline=¨cd /home/lance/MyDownloads¨
alias shared=¨cd /home/lance/Shared¨
alias whereami=pwd
alias whereareyou=pwd
alias where=pwd
alias whoareyou=whoami
alias full=¨avgscan -H /home/lance¨

it still does not work I have done some old post on this at [http://ubuntuforums.org/showthread.php?p=7145538#post7145538](http://ubuntuforums.org/showthread.php?p=7145538#post7145538) I now have a new problem when i open a terminal i have

bash: alias: apt-get: not found
bash: alias: update¨: not found
bash: alias: apt-get: not found
bash: alias: upgrade¨: not found
bash: alias: /home/lance¨: not found
bash: alias: /home/lance/Documents¨: not found
bash: alias: /home/lance/downloads¨: not found
bash: alias: /home/lance/MyDownloads¨: not found
bash: alias: /home/lance/Shared¨: not found
bash: alias: -H: not found
bash: alias: /home/lance¨: not found
lance@bermudez:~$ 

what am i doing wrong? sence i changed my (´) to (¨) nun of my alias work now.

---

### Post by llamabr on 2009-04-26
That's strange.  Where are you putting these?

It looks like toward the bottom you missed some quotes, namely with the pwd commands.  Try just putting in one at a time, and see if it works.

---

### Post by llamabr on 2009-04-26
What do you mean you're running avg 8.5?  isn't that a windows based virus blocker?  Why are you running it, and why is it relevant to your post?

---

### Post by lance bermudez on 2009-04-26
in /home/lance/.bash_aliases is where they are being put. I have found out what my problem is my(¨) looks as shown and i have to hold shift and press the key twice for the mark to display so i copied and pasted the (") from the help form and things now work right. I think I might need to reinstall my keyboard does any one know how to do that I need a gui and for more info I using a acer aspire 4720z labtop. i have attached my aliases in case anyone wants to look at them. thank you for all your help everyone.

---

