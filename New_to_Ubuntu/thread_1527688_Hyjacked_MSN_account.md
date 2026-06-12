---
title: "Hyjacked MSN account??"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Gone fishing on 2010-07-09
My sister has been sending me spam email for a couple of months.

I finally had the opportunity to have a look at her PC expecting a compromised XP Box. I was somewhat supprised to find she was running Ubuntu (jaunty).

Looking a little further she wasn't running a mail client like Thunderbird but Hotmail online using Mozilla. 

I've concluded that it is vanishingly unlikely that she has a virus and either her address is being spoofed by a compromised XP box that has her address, or her MSN hotmail account has been hjacked. Looking at the headers of one of the spam emails it seems that the latter has happened - the mail is comming from hotmail. Is this common?

Her password was her village name not the best but 10 digits and difficult for a bruteforce attack.

Any thoughts?

---

### Post by themusicalduck on 2010-07-09
Pretty much in all cases you just need to change the password. If a spambot has got hold of the password then it can use the email for spamming.

This happened to me a few months ago and I always run Ubuntu. I just changed the password and I haven't had it happen since.

edit: my password was a combination of random letters and numbers too, so a strong password! I had heard a few days before about a bunch of hotmail accounts that had been compromised, so I think getting a virus isn't the only way to get your account hijacked.

---

### Post by freddiespagheti on 2010-07-09
Actually, this happened to me just a couple days ago but with gmail. If she didn't fall for a phishing attack then my guess is that she uses an online service, provided her email address, and used the same password as for her email account. Then someone malicious hacked into the non-malicious website and stole her info. 

It's just a theory but I can't think of how else it might have happened other than phishing.

All she has to do is change her password, security questions, and be sure there is no automatic forwarding to unfamiliar address or POP or IMAP access etc. 

Also, maybe she should switch to gmail because when mine was compromised, they automatically locked it after just 4 spam messages were sent. All I had to do to get in was answer a security question and reset my password.

---

### Post by ov3rcl0ck on 2010-07-09
There were kinda recent adobe reader exploits that were cross platform that could comprise the browsers, but then again they never found anything in the wild using that vulnerability before they found and patched it. It could be some kind of browser hijacking but very very unlikely.

Most plausible attacks would be either getting her email and spoofing her email address, which Thunderbird would tell you that it was spoofed, or they somehow obtained the account password through means of phishing or similar scams.

Change the password, and honestly if you're worried about browser hijackings then use Google Chrome. Chrome sandboxes each tab, and each plugin, making it more secure and more stable.

Theres an article about it being possibly the most secure browser out there, it was the only browser untouched by exploits in a Def Con contest.

---

### Post by mcduck on 2010-07-09
Hotmail isn't really that secure, accounts get cracked rather randomly just for spamming purposes. And if your sister has ever accessed it on some public machine (and didn't remember to clear browser cache afterwards) that could have caused the problem as well.

The first step, as already suggested, is to try to change the password. If you aren't able to do that then read this page for more instructions: [http://explore.live.com/windows-live-account-account-hacked-faq]("http://explore.live.com/windows-live-account-account-hacked-faq")

The second step is to check *every* other web site and service where she might have used the same password, and change their passwords as well.

(I recently helped a friend whose hotmail account was cracked and used for spamming, she hadn't actually used hotmail itself for years but used the same account for Messenger. Her (Windows) computer proved to be clear of any viruses and spyware, so it seems to me that either the account was simply cracked with brute force or through some Messenger vulnerability. Simply changing the account password solved the problem.)

---

### Post by Gone fishing on 2010-07-09
Thanks for the replies - I wasn't worried about a browser attack but deleted the .mozila directory anyway. I changed her password to a 18 digit mix case password so I think things will stop. 

I don’t think her address is being spoofed as the full mail headers look kosher. It just seems odd that the account was hjacked.

---

### Post by bacardiandwatermelon on 2010-07-09
My account sent out a whole lot of spam a couple of months back, it was due to me using live messenger on a friends infected machine. Have since closed though. Not worth the effort.

---

### Post by ov3rcl0ck on 2010-07-09
> **mcduck said:**
> Hotmail isn't really that secure, accounts get cracked rather randomly just for spamming purposes. And if your sister has ever accessed it on some public machine (and didn't remember to clear browser cache afterwards) that could have caused the problem as well.

The first step, as already suggested, is to try to change the password. If you aren't able to do that then read this page for more instructions: [http://explore.live.com/windows-live-account-account-hacked-faq]("http://explore.live.com/windows-live-account-account-hacked-faq")

The second step is to check *every* other web site and service where she might have used the same password, and change their passwords as well.

(I recently helped a friend whose hotmail account was cracked and used for spamming, she hadn't actually used hotmail itself for years but used the same account for Messenger. Her (Windows) computer proved to be clear of any viruses and spyware, so it seems to me that either the account was simply cracked with brute force or through some Messenger vulnerability. Simply changing the account password solved the problem.)

Hotmail restricts password attempts and also uses HTTPS... wasn't bruteforce and/or dictionary attack, 100% sure of that.

They should be good now, 18 length password with a 2second delay between each attempt at least, will take about 2 years for bruteforce and about 3weeks for dictionary attack, but still a 18 character password probably won't be in a wordlist..

---

