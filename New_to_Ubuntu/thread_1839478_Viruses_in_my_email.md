---
title: "Viruses in my email"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by Rrory on 2011-09-05
I'm running Narhwal & today my yahoo email was highjacked for spam. What's going on? I thought Linux was virus free. And what should I do?
rory

---

### Post by alegomaster on 2011-09-05
> **Rrory said:**
> I'm running Narhwal & today my yahoo email was highjacked for spam. What's going on? I thought Linux was virus free. And what should I do?
rory

Can you give more detail. I have almost no clue what happened.

Edit: Did someone get on your account and started to send spam?

---

### Post by SavageWolf on 2011-09-05
What do you mean "hijacked for spam"? The OS itself is highly resistant to viruses, but that won't stop people trying! (Mostly they fail)

---

### Post by haqking on 2011-09-05
> **Rrory said:**
> I'm running Narhwal & today my yahoo email was highjacked for spam. What's going on? I thought Linux was virus free. And what should I do?
rory

your Linux has no control over your webmail with yahoo.

Linux does not suffer from Viruses Like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords etc.

Common sense, dont tell your system you want it to do something unless you are sure etc.

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox etc.

Also look at apparmor for profiling your applications and there privelege

See below staring with Bodhi.Zazen overvie3w of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

then here for AV information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)


as for your problem we need more information about what you mean ?

---

### Post by alegomaster on 2011-09-05
> **SavageWolf said:**
> What do you mean "hijacked for spam"? The OS itself is highly resistant to viruses, but that won't stop people trying! (Mostly they fail)

I think somebody cracked his account and now is using it to send spam. In that case he would have to change passwords.

Also your signature is really fitting for this thread.

---

### Post by Rrory on 2011-09-05
Sorry to be obscure. I just found my entire yahoo addresss list was taken over by someone/something which sent various types of spam to all my friends. Is it spoofing?

I did open a windows doc last night with macros, but I stopped the macro. I'm a bit confused, do I need to change my yahoo p-word?

---

### Post by haqking on 2011-09-05
> **Rrory said:**
> Sorry to be obscure. I just found my entire yahoo addresss list was taken over by someone/something which sent various types of spam to all my friends. Is it spoofing?

I did open a windows doc last night with macros, but I stopped the macro. I'm a bit confused, do I need to change my yahoo p-word?


Well that doesnt mean Linux has a virus (see my above links)

Spoofing is pretending to be someone you are not.  Such as i can send an email right now pretending to be [EMAIL="whoever@whoever.com"]whoever@whoever.com[/EMAIL] even though it didnt come from them.  And yes change your password as a precautionary measure.

Was the windows doc opened in windows or in Linux ?

---

### Post by alegomaster on 2011-09-05
> **Rrory said:**
>  I'm a bit confused, do I need to change my yahoo p-word?

Whenever something weird is going on any account of yours,_**CHANGE THE PASSWORD**_. I believe you might have given away your username and password somewhere. I never heard of a macro doing something like this before, but I might not know because I dont care about macros at all. But remember be safe, and make sure that you dont go on anything suspicious. 

Sorry if I sounded a bit mean to you, but people have to learn and pointing out the steps they should do would help.

Edit: I got ninja by haqking. I need to type faster. On a side note anyone knows any opensource teach how to type programs on linux.

---

### Post by kerry_s on 2011-09-05
> **Rrory said:**
> Sorry to be obscure. I just found my entire yahoo addresss list was taken over by someone/something which sent various types of spam to all my friends. Is it spoofing?

I did open a windows doc last night with macros, but I stopped the macro. I'm a bit confused, do I need to change my yahoo p-word?

you need to go to yahoo.com & change your password, it was probably hacked server side, meaning they hacked yahoo, nothing to do with your os or computer, it's in the cloud.

same thing happened to my mom on yahoo to, so put a long complicated password(upper & lower case with numbers) you can remember.

---

### Post by Rrory on 2011-09-05
Okay may thanks for the clear explanation, it was the cloud server: and now p-word changed. 

Don't worry about being mean if it helps others, I'm extremely careful with my p-words & never give them out.

---

### Post by alphacrucis2 on 2011-09-05
> **Rrory said:**
> Okay may thanks for the clear explanation, it was the cloud server: and now p-word changed. 

Don't worry about being mean if it helps others, I'm extremely careful with my p-words & never give them out.


One way the spammers get such user credentials is via phishing scams. I even came across a case were a forum administrator got fooled into revealing his ucode/password. He received a bogus email purporting to be from a user pointing out an issue they were having on the forum with a link to the supposed problem thread. The link took them to a fake copy of the forum requesting a login. The guy entered his admin usercode and password without paying attention to the actual URL. If you had an email claiming to be from yahoo saying some nonsense such as verify your account details then beware (even more so if it claimed to come from your bank).

---

### Post by xx58 on 2011-09-05
Try install windows based program exe. It is not possible. Same reason Virus cannot be in Linux operating system.Linux are like AntiVirus for Virus.

---

### Post by whatthefunk on 2011-09-05
> **xx58 said:**
> Try install windows based program exe. It is not possible. Same reason Virus cannot be in Linux operating system.Linux are like AntiVirus for Virus.

Unless of course its a Linux specific virus.  Or a cross-platform virus.  Im sure you could find a .deb file out there somewhere that will do some serious damage to your system.

---

### Post by BBQdave on 2011-09-06
This is curious?  I have a yahoo email account and I use that address to join facebook (awhile back).  A couple months ago I started getting random chat-friend invites on both yahoo and facebook from unknown (questionable) sources.  Maybe this is usual for free accounts.  And my accounts have not been hijacked (to send advertisements and shopping invites) to friends.  Though friends on facebook have been hijacked, about one a month (3 to this point in time).  I figure the hijackers have my yahoo email address and general info on facebook.  Am I more of a target because I am grouped (friends) to compromised accounts?

---

### Post by fdrake on 2011-09-06
were those email received in the inbox or in the spam section? if they are threated as spams than someone knows your email address and is trying to send email trought an email server (like sendmail) with your yahoo id . If it is received in the iinbox there are 2 cases:
1. your account has been compromised.
2. the attacker is using valid pseudo-headers to trick the spam filter and make it believe it's actually your email.

---

### Post by 1clue on 2011-09-06
Wow guys, some of you need to take spammer 101.

First, it's not good enough to change your password.  Change it to something that's not part of your name as seen in your profile, or any p53ud0-3nc0d3d variant of it.  Or the name of your kids, or parents, or anybody else you ever mention.  Best yet, type your password into a password quality checker and don't use it if it's not strong.  Years ago I started copying segments of a DSA encryption key, so each password has nothing to do with any language.  The more characters you can remember the better the password, but don't write the darn thing down and put it under your keyboard.  Or in a file on the computer someplace.

Any email you use on a forum will be scanned and used in spam.  The spammer doesn't even need to have an account with your forum, all they need to do is use Google and grab anything out of the history that looks like an email address.

---

### Post by jmate24 on 2011-09-06
suggestions for your problem:

1. do not link accounts such as email and facebook or twitter.
2. use only one email for each facebook and twitter.
3. set facebook and twitter to notify you by cell phone when someone logs into your accounts and have the phone to be able to verify that it was you logging in.

3. if you do not know someone on facebook or twitter don't add them only add the people you know and trust.
4. block anyone on facebook and twitter that has a grudge against you out in the real world.
5. screen your friend invites carefully.
6. if you can run a free internet background check on your friends.
7. don't give money, passwords, email addresses, street addresses, or phone numbers to anyone asking for them on facebook or twitter and don't put them on facebook or twitter for everyone to see.
8. don't use Apps and games on facebook, twitter or your email provider.
9. Use a hardware and software firewall besides the one your ISP issues you and make sure your anti-virus software is up to date. I use nProtect and it works the best just be sure to block your file and print sharing if you are not using it to share files with windows or linux.
10. finally, run windows in linux with either virtualbox or vmware that way you are protected from most hack-jobs unless you download a virus on to windows.

jmate24

---

### Post by fractalman on 2011-09-06
> **alegomaster said:**
> Whenever something weird is going on any account of yours,_**CHANGE THE PASSWORD**_. I believe you might have given away your username and password somewhere. I never heard of a macro doing something like this before, but I might not know because I dont care about macros at all. But remember be safe, and make sure that you dont go on anything suspicious. 

Sorry if I sounded a bit mean to you, but people have to learn and pointing out the steps they should do would help.

Edit: I got ninja by haqking. I need to type faster. On a side note anyone knows any opensource teach how to type programs on linux.



I have just started playing with python, i started this thread a few days ago, plenty of info for learning to  programme

[http://ubuntuforums.org/showthread.php?t=1836517](http://ubuntuforums.org/showthread.php?t=1836517)

---

### Post by SavageWolf on 2011-09-06
Is it me or is everyone on this site paranoid about being attacked? While I do think FB's permissions system is a bit stupid, I think that hiding in a paper bag is stupid...

If you are using a system that lets you talk to the rest of the world, don't post private information... I just use my Twitter for generic ranting at everyone and everything. Not for talking about who I had sex with or where I am going on holiday or anything...

Also, don't use the same password for everything! I use GPass and randomly generate passwords for everything I use!

I wonder... An idea comes to mind... Would it be possible for me to create an extension/addon that randomised passwords and auto-updated them every week or so, and automatically logged you in? I should do that...

---

### Post by whatthefunk on 2011-09-06
I think that changing passwords every week is a little excessive.  Ive changed passwords once in the last decade and my mail account has never been compromised.  I make passwords based off words, but unrecognizable as words.  This way I an remember them but also have a good password.  I usually take two words, lets say "coffee" and "like" and put them together with a random number between them.  coffee5like.  I then make a couple of the letters capital. coFFee5Like.  Then I change a couple letters to numbers.  c0FFe35Lik3.  Then, if the system allows special characters, I add a special character and a number on the end so that my final password looks something like this: c0FFe35Lik3_9  The whole point of a password is to have something that is extremely difficult to crack (having many characters of different types) **that you can remember.**  Having a random password generator generate something like this 8f-Pikk39knaPLC>0.2385jIo91 is great except that Ill never be able to remember it and will always have to rely on some sort of password program or encrypted file somewhere.

---

### Post by 1clue on 2011-09-06
> **SavageWolf said:**
> I wonder... An idea comes to mind... Would it be possible for me to create an extension/addon that randomised passwords and auto-updated them every week or so, and automatically logged you in? I should do that...

This negates everything you gain by changing passwords regularly.  You still have a single point of failure which, if compromised, exposes every account you have.

[QUOTE=whatthefunk]c0FFe35Lik3_9[/quote]

That's just about like having a plain text password.  Replacing the letters with numbers does almost nothing to any organized password cracker.  You're replacing letters with numbers that either look like the letters, and that's been happening since green screens were new.

On top of that, the use of English language words makes the password even easier to hack.

---

### Post by BBQdave on 2011-09-06
I agree with SavageWolf, if you are going to communicate with the outside world, do not be paranoid.  But speaking in general and not detailing specifics is a good idea.  Though it is just you and your computer, you are viewed by many.

---

### Post by whatthefunk on 2011-09-07
> **1clue said:**
> That's just about like having a plain text password.  Replacing the letters with numbers does almost nothing to any organized password cracker.  You're replacing letters with numbers that either look like the letters, and that's been happening since green screens were new.

Then Ive been using unsafe passwords for a decade and have still never had an account compromised.  I think some of us are overly paranoid...

---

### Post by 1clue on 2011-09-08
I have never met somebody who hasn't described me that way after seeing one of my "temporary" passwords, at least after I saw the light.

I have had two accounts hacked, but that was before I had any sort of procedure for passwords.  I used one much like you have described and it had 8 characters, I thought it was pretty solid, and AFAICT it was brute forced.  The log showed a huge number of ssh attempts, and then finally success.

Every password I issue to a user at work is generated by a random text generator having nothing to do with any human or computerized language.  Almost every one contains 4 character groups, sometimes just 3.  Every one is at least 12 characters.

My personal passwords are larger than that.  I have several, and I spread them across my important accounts and rotate them through a queue such that every account gets changed frequently enough to satisfy most IT admins, but such that I don't have to remember quite so many passwords at once.

---

### Post by Rrory on 2011-09-15
Wow, I'm the original poster, my yahoo account was hacked again today. I changed my p-word that day & now it's been hacked again. What's going on, where is it going on. I had to explain to a bunch of groups that my laptop isn't infected I have Linux. 
thanks
rory

---

### Post by SeijiSensei on 2011-09-15
[http://ubuntuforums.org/showpost.php?p=11247336&postcount=9](http://ubuntuforums.org/showpost.php?p=11247336&postcount=9)

Substitute "Yahoo!" for "MSN" and "random country" for "Argentina" in the posting above.

---

### Post by David Andersson on 2011-09-15
You say someone is sending spam emails to your friends. Are you sure your account is the sender of those emails? Even if you "appear" to be the sender, your friends need to investigate the hidden headers in their received emails to see if you really are.

Maybe someone just have found your email-address and the email-addresses of your friends.

---

### Post by agillator on 2011-09-16
Rrory: do have your friends check the full headers of the emails. They are probably just using your name, not your account. That is not difficult to do.

As for passwords, I agree with those who say make them as complicated as possible. A good way I have found is to think of a sentence I can remember that includes alpha and numeric characters, change a few of the obvious words to special characters, then take the first letters, third letters, whatever and those become the password. For example, 'I might someday wish to take a World Cruise with my wife'  might become Imsw.t1WCwmw. That should be a fairly strong password, but easy to remember.

About being paranoid, I'm afraid I believe in being paranoid when dealing with the internet. However I also believe in moderation.

---

### Post by dfarrell07 on 2011-09-16
The best overall tip with passwords is to use strange members of the character set, as well as numbers and CAP letters. Don't simply replace words with l33t, that is anticipated by rainbow tables (password crackers). Also, don't use numbers on the start or end of passwords, that is also much more likely to be brute forced. Examples of good chars to include: <>^%~`|{}. You can check out the following link to see some databases that have been hacked, and the passwords released. They give in-the-wild data about which passwords people actually use. This kind of thing is what rainbow tables are built from, so avoid anything like any of the ones on that list. Any password you see on that list will be brute forced in seconds. Make sure to checkout the breakdown by chars - it is very helpful.

[http://bit.ly/ohMfZ9](http://bit.ly/ohMfZ9)

---

