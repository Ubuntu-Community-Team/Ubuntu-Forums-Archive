---
title: "Can I limit profiles displayed at login to just one?"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-06
I have a Toshiba Satellite A205 notebook that I've set up w/ Ubuntu v10.04 LTS. I currently have 3 profiles set up on the machine:
1) The original profile (admin level)
2) A user profile (limited, no admin access),
3) An admin profile for me to use during setup of the machine.

When the setup process is finished, just before handing the machine over to my mother for her use, I'd like to be able to make the only profile displayed on the initial login screen be the 2nd profile. But, I'd like to make sure the other 2 profiles remain available for potential future maintenance of the machine (updates & upgrades, for example). When the machine is in her possession, I'd provide her with knowledge (in written form) of how to access the hidden profile #1, and the password for it. That way, if anybody other than me goes to do maintenance on the machine, they'd have profile #1 to work with. Profile #3 would remain hidden & strictly mine, since I'd be leaving my email account info and other personal data intact upon it. The real purpose of my intent here, is to make it as simple as possible for her to login; few options, few choices; i.e., click on the only name visible, type in password, and press <Enter>.

Is it possible for me to set it up that way? And if yes, then exactly how would I do that? TIA.

---

### Post by Rex Bouwense on 2011-08-06
I'm not sure if you can do what you describe but you can configure the log-in process to automatically log her in without using the password and allow so many seconds for someone else to log in first i.e. you.  Will that work?

---

### Post by scruffyeagle on 2011-08-06
> **Rex Bouwense said:**
> I'm not sure if you can do what you describe but you can configure the log-in process to automatically log her in without using the password and allow so many seconds for someone else to log in first i.e. you.  Will that work?

Well, sure that would work - but, it's a lot like leaving the front door to her house unlocked all the time. She's told me she intends to drag this thing around with her, so I think password protection isn't something that can be skipped. If it turns out the optimum setup isn't possible, then I'll just leave the login list the way it is. Thanks for the reply, though.

---

### Post by haqking on 2011-08-06
> **scruffyeagle said:**
> Well, sure that would work - but, it's a lot like leaving the front door to her house unlocked all the time. She's told me she intends to drag this thing around with her, so I think password protection isn't something that can be skipped. If it turns out the optimum setup isn't possible, then I'll just leave the login list the way it is. Thanks for the reply, though.

you can remove the show list of users from the login screen by taking the tick out from the preferences on loigin scren under system<administration ?

Is this what you mean ?

---

### Post by scruffyeagle on 2011-08-06
> **haqking said:**
> you can remove the show list of users from the login screen by taking the tick out from the preferences on loigin scren under system<administration ?

Is this what you mean ?

No, definitely not. I just tested it, and it entirely skipped the login process.

This little test did teach me one important thing, though. If somebody else was to work on the machine using the admin profile #1, they could use that utility (while in profile #1) to set up booting into my admin profile without needing to know my password. The only way I can keep my files & email private in that situation, is if I can encrypt my home directory. I don't know at the moment, whether it's possible to do that now, or whether the encryption of home needs to be arranged during creation of the profile. In which case, I'd need to start a new profile w/ encrypted home, and go through the setup of email (etc.) all over again to tweak it the way I like it. That would be a pain in the you know what.

---

### Post by Guruprasad on 2011-08-06
Just try changing the uid of the user to less than 1000. You can do it from system > Administration > User and Group. There are many users listed but only user with less than 1000 uid get listed.

I have not tried this method but I read it somewhere.

---

### Post by haqking on 2011-08-06
> **scruffyeagle said:**
> No, definitely not. I just tested it, and it entirely skipped the login process.

This little test did teach me one important thing, though. If somebody else was to work on the machine using the admin profile #1, they could use that utility (while in profile #1) to set up booting into my admin profile without needing to know my password. The only way I can keep my files & email private in that situation, is if I can encrypt my home directory. I don't know at the moment, whether it's possible to do that now, or whether the encryption of home needs to be arranged during creation of the profile. In which case, I'd need to start a new profile w/ encrypted home, and go through the setup of email (etc.) all over again to tweak it the way I like it. That would be a pain in the you know what.

it shouldnt do that, i think you might have said to automatically login which isnt what you want.  By removing the tick from show all users it should show a login prompt asking for username and not showing any users on the system which is what is does show by default.

> **Guruprasad said:**
> Just try changing the uid of the user to less than 1000. You can do it from system > Administration > User and Group. There are many users listed but only user with less than 1000 uid get listed.

I have not tried this method but I read it somewhere.

yes you can do this but you have to check the UID is not used as UID <1000 are used by the system so just choosing a random number below 1000 could trash something ;-)

---

### Post by scruffyeagle on 2011-08-06
I thought something wasn't clicking here... You advise me to "remove the tick". Unfortunately, I don't have a checkbox w/ tick in the utility. Instead, I have 2 options w/ round bullets; you can only choose by toggling between one or the other, not check & uncheck w/ tick mark. One is to show a login screen w/ list. The other is to boot automatically, w/ options to select which user and an optional delay for selecting someone else.

I think I'll try the < 1000 idea, but I suspect that going less than 1000 will have the effect of hiding users from the login menu, not making them available for it. (And yes, I'll be cautious about the exact # I choose!) I also suspect that once a user is hidden in that manner, they won't be accessible from the login page - but, I'll try it, and see what happens.

---

### Post by haqking on 2011-08-06
> **scruffyeagle said:**
> I thought something wasn't clicking here... You advise me to "remove the tick". Unfortunately, I don't have a checkbox w/ tick in the utility. Instead, I have 2 options w/ round bullets; you can only choose by toggling between one or the other, not check & uncheck w/ tick mark. One is to show a login screen w/ list. The other is to boot automatically, w/ options to select which user and an optional delay for selecting someone else.

I think I'll try the < 1000 idea, but I suspect that going less than 1000 will have the effect of hiding users from the login menu, not making them available for it. (And yes, I'll be cautious about the exact # I choose!) I also suspect that once a user is hidden in that manner, they won't be accessible from the login page - but, I'll try it, and see what happens.

mmm what version are you using ?

also hiding the user with less than <1000 will still be able to login by manually supplying credentials, it just means the user wont be displayed, however they will still exist in /etc/passwd and /home directory will exist etc when looking for them forensically speaking.

you can do a 

cat /etc/passwd to find used UID's

but this really isnt the best way to do it.

I a wondering why you dont have the option to turn off list all users.

however this should remove the list using terminal:

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set /apps/gdm/simple-greeter/disable_user_list True

---

### Post by bodhi.zazen on 2011-08-06
> **scruffyeagle said:**
> I thought something wasn't clicking here... You advise me to "remove the tick". Unfortunately, I don't have a checkbox w/ tick in the utility. Instead, I have 2 options w/ round bullets; you can only choose by toggling between one or the other, not check & uncheck w/ tick mark. One is to show a login screen w/ list. The other is to boot automatically, w/ options to select which user and an optional delay for selecting someone else.

I think I'll try the < 1000 idea, but I suspect that going less than 1000 will have the effect of hiding users from the login menu, not making them available for it. (And yes, I'll be cautious about the exact # I choose!) I also suspect that once a user is hidden in that manner, they won't be accessible from the login page - but, I'll try it, and see what happens.

Changing the user number to less then 1000 has worked well for me in the past. The user name will not be displayed, but you can enter the name manually.

Yes you need to check the uid of other users, but that is rather trivial. If for some reason < 1000 does not work , go with < 500 .

---

### Post by scruffyeagle on 2011-08-06
_**haqking**_: I'm running Ubuntu v10.04 LTS. Thanks for the tip re. cat /etc/passwd. This exactly what I needed before proceeding, in order to make sure that the # I pick isn't already in use. Although, I used
```
cat /etc/passwd | less
```.

**_bodhi.zazen_**: Thanks for the tip re. < 500. I'll be testing using 400, now that I've checked & made sure it's not currently in use.

---

### Post by scruffyeagle on 2011-08-06
Quick update: I used the "Users & Groups" utility to change profile #1's # to 400. Checking, I found that it didn't show up in the login list. That seemed great - but, trying to log in, resulted in authentication failure. Logged in via profile #3, called up "Users & Groups" - shock. Profile #1 wasn't there any more. I ended up using
sudo gedit /etc/passwd
to edit passwd directly. Changed 400 back to 1000, and saved it. Called up "Users & Groups". Found that Profile #1 was back in the list. Changed it from 1000 to 1003, and exited. Opened it up again, and changed it back to 1000. Which, is where I've left it now.
The reason I opened, changed, saved, opened, changed, and saved is this: I thought it was possible that if I didn't change it via the "Users & Groups" utility, there could be some trivia of recordkeeping re. the change that wouldn't be updated. The reason I did it twice, is I thought there was a chance that some of that recordkeeping might not be finalized until the utility closed; i.e., closing & opening again was the only way to be sure that possibility had been covered.

---

### Post by haqking on 2011-08-06
> **scruffyeagle said:**
> Quick update: I used the "Users & Groups" utility to change profile #1's # to 400. Checking, I found that it didn't show up in the login list. That seemed great - but, trying to log in, resulted in authentication failure. Logged in via profile #3, called up "Users & Groups" - shock. Profile #1 wasn't there any more. I ended up using
sudo gedit /etc/passwd
to edit passwd directly. Changed 400 back to 1000, and saved it. Called up "Users & Groups". Found that Profile #1 was back in the list. Changed it from 1000 to 1003, and exited. Opened it up again, and changed it back to 1000. Which, is where I've left it now.
The reason I opened, changed, saved, opened, changed, and saved is this: I thought it was possible that if I didn't change it via the "Users & Groups" utility, there could be some trivia of recordkeeping re. the change that wouldn't be updated. The reason I did it twice, is I thought there was a chance that some of that recordkeeping might not be finalized until the utility closed; i.e., closing & opening again was the only way to be sure that possibility had been covered.


you could have saved yourself the hassle with the command i supplied earlier which would just hide your list without changing UID's.

also when using graphical apps like gedit then you shouuld use gksudo and not sudo.

but at least you have it sorted

---

### Post by scruffyeagle on 2011-08-08
> **haqking said:**
> you could have saved yourself the hassle with the command i supplied earlier which would just hide your list without changing UID's.

also when using graphical apps like gedit then you shouuld use gksudo and not sudo.

but at least you have it sorted

Back again... It turns out I didn't have it repaired as well as I'd thought. When I started up the machine today, I decided to work with my profile #1. When it started up KDE, there was a major failure to find services. (I didn't write down the details, and have forgotten exactly what it said.) It seemed pretty fundamental to me, and I believed it was connected with my messing around with user ID's (etc.). I didn't have a clue how to fix it, and figured it would take more time than I was willing to invest, tracking down help and following advice - so, I restarted the machine, logged in as my profile #3, and deleted profile #1 entirely. (There was nothing in it, that I couldn't afford to lose.)

After that, I rebooted, logged into KDE as profile #3, and recreated profile #1; slightly different name, but same privileges, same UID, etc. Since I did this, there's been one small change in the system's behavior: The sequence of the names displayed in the login list never changes, regardless of how I shuffle around the sequence of UID's. The 3 names in the list are now shown in the order of Profile #2 (UID 1002), Profile #1 (UID 1001), & Profile #3 (UID 1003). Just for the sake of knocking out possibilities, I'll mention that not only does this not follow UID numerical order, it also doesn't follow alphabetic or length of names order. This is disadvantageous, because the cursor's initial appearance puts it hovering above the 2nd entry; i.e., profile #1, not profile #2.

I feel I should inquire for more detail, before using the command you supplied in your earlier post. If I use that command, how would it affect the login sequence? Can you describe the sequence that would be seen when the computer starts up, the time frame for user reactions, etc.? Also, it would be useful to ahead of time, how to reverse the command if I decide I don't like the result. My guess (tell me if I'm right or wrong) is that to reverse the command one would repeat entering it but substitute "FALSE" for "TRUE".

Thanks for correcting me, re. use of gksudo instead of sudo when using graphic apps from terminal. (This means I edited incorrectly, when I tried to correct that list yesterday.) Hopefully, I'll remember this in the future!

---

### Post by scruffyeagle on 2011-08-08
**_bodhi.zazen_**: I was wondering if you had any thoughts about the security loophole I found and mentioned in post #5 of this thread. In a case where there are 2 administrator profiles on the same machine, is there any way to safeguard the contents of either one against being viewed (&/or tampered with) by the other?

---

### Post by Wim Sturkenboom on 2011-08-08
It's not a security loophole in my opinion. Admins need to trust each other. As well as that users need to be able to trust the admin.

As you stated, encryption will prevent viewing and modifying, but a second admin can further do whatever he/she likes (including disabling your account or removing you as well as installing keyloggers to get to your password). It might take some hacking, but it is doable if one is determined.

---

### Post by scruffyeagle on 2011-08-08
> **Wim Sturkenboom said:**
> It's not a security loophole in my opinion. Admins need to trust each other. As well as that users need to be able to trust the admin.

As you stated, encryption will prevent viewing and modifying, but a second admin can further do whatever he/she likes (including disabling your account or removing you as well as installing keyloggers to get to your password). It might take some hacking, but it is doable if one is determined.

Yes, it's true that a determined & knowledgeable hacker with Admin powers could pretty well do whatever he/she pleased. But, why make it quick & easy? Knowing about this loophole, and given Admin powers, I could be into some other Admin's files in less than a minute (inclusive of reboot time). In the case of the machine I've been discussing, I'll be handing it over to my mother within the week - and, won't be using my Admin profile except for those (hopefully infrequent) occasions when her system needs maintenance. If for some reason I'm gone and she has someone else work on the machine, it would be smart to at least make it difficult for that unknown person to access my files.

---

### Post by bodhi.zazen on 2011-08-08
> **scruffyeagle said:**
> **_bodhi.zazen_**: I was wondering if you had any thoughts about the security loophole I found and mentioned in post #5 of this thread. In a case where there are 2 administrator profiles on the same machine, is there any way to safeguard the contents of either one against being viewed (&/or tampered with) by the other?

IMO hiding the list of users on a system in the login screen does very little, if anything, to increase security.

Users still need a password, to "log in" , worse physical access == root access.

If you want to increase security you will need to look at options such as encryption or selinux (confine users).

But if a user has admin power, that implies root access, and the only tools that can restrict root are encryption and apparmor/selinux.

You can obtain a list if uses in the system in many many ways, more so if you are in the admin group.

---

### Post by scruffyeagle on 2011-08-08
> **bodhi.zazen said:**
> IMO hiding the list of users on a system in the login screen does very little, if anything, to increase security.

Users still need a password, to "log in" , worse physical access == root access.

If you want to increase security you will need to look at options such as encryption or selinux (confine users).

But if a user has admin power, that implies root access, and the only tools that can restrict root are encryption and apparmor/selinux.

You can obtain a list if uses in the system in many many ways, more so if you are in the admin group.

Actually, my desire to hide users at the login screen is strictly to make it as simple as possible for my mother to log in when she has the machine. If there's only one option, or better yet if the login is prepped for her to just start typing in her user profile's password, that would be optimum. My discussing the Admin powers thing is a separate issue entirely.

---

### Post by bodhi.zazen on 2011-08-08
> **scruffyeagle said:**
> Actually, my desire to hide users at the login screen is strictly to make it as simple as possible for my mother to log in when she has the machine. If there's only one option, or better yet if the login is prepped for her to just start typing in her user profile's password, that would be optimum. My discussing the Admin powers thing is a separate issue entirely.

Why not just enable auto-login for her ?

---

### Post by scruffyeagle on 2011-08-08
> **bodhi.zazen said:**
> Why not just enable auto-login for her ?

She intends to take the Toshiba notebook with her when she goes places, including when she goes to work. She's not security oriented, and I just know she's going to leave it unattended now & then. She works as an organist for a church, and goes there several times a week for work & practice sessions. Although I'm sure most of the people in her church are trustworthy, I can't personally vouch for each of them. And, I don't believe that just because somebody is in the church building is grounds for trusting their integrity. Therefore, I should set the computer up with a standard level of security precautions for a public place - which, I believe, includes requiring a password for access.

---

### Post by bodhi.zazen on 2011-08-08
> **scruffyeagle said:**
> She intends to take the Toshiba notebook with her when she goes places, including when she goes to work. She's not security oriented, and I just know she's going to leave it unattended now & then. She works as an organist for a church, and goes there several times a week for work & practice sessions. Although I'm sure most of the people in her church are trustworthy, I can't personally vouch for each of them. And, I don't believe that just because somebody is in the church building is grounds for trusting their integrity. Therefore, I should set the computer up with a standard level of security precautions for a public place - which, I believe, includes requiring a password for access.

Well, honestly you should ask her what she wants rather then forcing a security feature on her.

---

### Post by Wim Sturkenboom on 2011-08-09
> **scruffyeagle said:**
> Yes, it's true that a determined & knowledgeable hacker with Admin powers could pretty well do whatever he/she pleased. But, why make it quick & easy? Knowing about this loophole, and given Admin powers, I could be into some other Admin's files in less than a minute (inclusive of reboot time). In the case of the machine I've been discussing, I'll be handing it over to my mother within the week - and, won't be using my Admin profile except for those (hopefully infrequent) occasions when her system needs maintenance. If for some reason I'm gone and she has someone else work on the machine, it would be smart to at least make it difficult for that unknown person to access my files.

An extra barrier will not hurt if you're concerned about your data. But as said, admins need to be able to trust each other. If you or your mom don't trust the admin, don't allow him/her on the system.

What is that data that you have on there?

Having said that, I would be more concerned about your mom's data and encrypt her home directory. She probably has more important and possibly more sensitive data on there than you have.

---

### Post by scruffyeagle on 2011-08-09
> **Wim Sturkenboom said:**
> An extra barrier will not hurt if you're concerned about your data. But as said, admins need to be able to trust each other. If you or your mom don't trust the admin, don't allow him/her on the system.

What is that data that you have on there?

Having said that, I would be more concerned about your mom's data and encrypt her home directory. She probably has more important and possibly more sensitive data on there than you have.

Well, I wasn't sure how long it would take for me to finish setting up the Toshiba. I'd spent about a week wrestling with learning Ubuntu, and no end was in sight. I was spending all my online time on that machine, so I set up an email profile in KMail and imported all my old OE email. There was lots of economic & personal data there (both about me, and about others), that I consider confidential. Not to mention, use of my email account. But now, it's a moot point. I decided last night to wipe out all my personal email & account data on the Toshiba. This evening, I used Bleachbit to overwrite all the empty space on the home partition. I wiped out the extra Admin profile, leaving only mine as Admin. So, that machine now has only 2 profiles; a basic user, and an admin. And, when I hand the machine over, I'll also hand over both passwords.

I definitely would like to encrypt her home directory, but I haven't figured out how to do that on an already installed home directory. Do you know what programs I'd need to use, &/or commands I'd need to type in?


_**bodhi.zazen**_: Asking her what she wants would just result in her asking me what's best, because she relies on my experience & judgment in these matters. Knowing this, it comes back to my responsibility to make a good decision, and then carry through on what I've decided.

---

### Post by Wim Sturkenboom on 2011-08-09
> 
I'd spent about a week wrestling with learning Ubuntu

I must admit that you're brave. No initial knowledge of Ubuntu and next setting it up for your mom.

Good luck in supporting it.

---

### Post by scruffyeagle on 2011-08-12
> **Wim Sturkenboom said:**
> I must admit that you're brave. No initial knowledge of Ubuntu and next setting it up for your mom.

Good luck in supporting it.

Hee, hee, hee! How hard can it be?
*(Just kidding!)*

Seriously, I've put in at least a hundred hours studying Ubuntu & Debian during the past month, with another 40 or 50 actually tinkering with Ubuntu installations during that month.

This is the way I see it:
1) I have an above average I.Q.
2) I have a fair understanding of how computer systems work in general.
3) I have 12 years of experience w/ Windows.
4) I see that a huge number of other people are using Ubuntu on a daily basis.
5) If average people can do it, then the only thing preventing me from doing it is the willingness to put out the time & effort to learn.
6) The resources for success are right at hand; i.e., there's a huge amount of documentation, and a busy community of users helping each other. (More likely than not, when I admit my general ignorance, they'll help me too.)
7) Her buying the notebook computer despite it not having an OS was my idea. If I'd failed to achieve a fully functional installation, then I'd have bought it from her at the price she paid.
8 ) I live less than a block away from her. If something does go wrong, I'm right at hand to jump in & fix it. I even have a spare (backup) desktop machine she could use while I'm servicing her notebook.

So, you see it's not bravery. It's that my assessment of the situation predicted eventual success, combined with my willingness to put out effort, and my willingness to accept the consequences in the event of failure.

---

### Post by bodhi.zazen on 2011-08-12
> **scruffyeagle said:**
> 3) I have 12 years of experience w/ Windows.


I would list that as a liability not an asset. Some of your windows experience may help, but most will not.

People think the because I run Ubuntu I must know how to fix windows, but I know very little about anything beyond windows XP with I use at work.

---

