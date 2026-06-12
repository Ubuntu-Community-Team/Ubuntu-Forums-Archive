---
title: "E-mail problem."
date: 2010-05-05
forum: New to Ubuntu
---

### Post by pensioner77 on 2010-05-05
I have just up-dated to ubuntu 10.4 without any apparent problems until I tried to send an E-mail using Thunderbird.It refused to send it "unable to authenticate SMTP server. (SMTP-AUTH),You have chosen to use authentication. 'untick Use name & password'" I have never used that sort of thing and I cannot find anything to un-tick. My server settings show --connection security--none and use secure authentication as not ticked.
I can only suppose that the Ubuntu up-date has upset something---can anyone advise and help.

---

### Post by pi24 on 2010-05-05
Try it at "Edit" / "Manage Profiles". Then select the last item (SMTP) from the list on the left, select your profile, and click on "Edit".

---

### Post by the.phantom on 2010-05-05
kinda a thunderbird trouble not ubuntu
but
in tbird
click edit
account settings
server settings ( on left)
and  set connection security to NONE
and un check below that "use secure connection"

then on the bottom left click the Outgoing server (smpt)
then on right click "edit"
and make sure it is set up the same as above\

hope this helps

---

### Post by pensioner77 on 2010-05-06
Thanks to pi24 & the.phantom, but I am still shut out of sending E-mails.
There does not seem to be a "Manage profiles" under the Edit. As I stated the Server settings are exactly as 'phantom'said---and these are also correct in the Outgoing server.
I agree it seems to be a Thunderbird problem, but it was OK before I up-graded to 10.04,and it is OK on my XP partion,so it definitely looks to be something to do with 10.04!!

---

### Post by lidex on 2010-05-06
> **pensioner77 said:**
> Thanks to pi24 & the.phantom, but I am still shut out of sending E-mails.
There does not seem to be a "Manage profiles" under the Edit. As I stated the Server settings are exactly as 'phantom'said---and these are also correct in the Outgoing server.
I agree it seems to be a Thunderbird problem, but it was OK before I up-graded to 10.04,and it is OK on my XP partion,so it definitely looks to be something to do with 10.04!!

'Edit>Account Settings' select 'Server Settings' on left for each account. OK I see what you're saying. Have you tried with a new profile?

---

### Post by pensioner77 on 2010-05-07
Thank you everyone; I think that the problem has occurred because ubuntu 10.04 up-grade also up-graded Firefox!! Although all my checks on the settings seemed to show no authenticity requirements, I have found that even though the Outgoing server shows authentication none when I pressed edit, it showed "name & password" as ticked,which of course when removed, all is back to normal.
Thanks again everyone for your patience and help.;)

---

