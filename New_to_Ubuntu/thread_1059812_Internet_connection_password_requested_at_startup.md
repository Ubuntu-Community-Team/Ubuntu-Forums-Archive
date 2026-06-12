---
title: "Internet connection password requested at startup"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Scubdup on 2009-02-04
Sorry. I can't find any solutions by searching.

Every time I start up my newly installed Ubuntu desktop I am asked to put in a password for my keyring so that the system can connect to the wifi.

Is there any way of having this happen automatically?

Thanks for any assistance.

---

### Post by mcduck on 2009-02-04
It happens automatically if you input your user name & password at login screen.

If you use automatic login you either need to input the keyring password manually, or remove the password (in Applications/Accessories/Passwords and Encryption Keys)

---

### Post by PriceChild on 2009-02-04
I 'think' you might need to change your keyring password to match your ubuntu user's password. I'm unfortunately not at my ubuntu machine atm so can't give exact instructions, but you will find the ability somewhere withing the seahorse application. Its at Applications > Accessories > Passwords & Encryption Keys. I think it is on the password tab.

---

### Post by Scubdup on 2009-02-04
Thanks guys. Looks like a unanimous vote for looking at Applications > Accessories > Passwords & Encryption Keys.

---

### Post by Scubdup on 2009-02-05
Well, the noob is back.

I deleted the keys and restarted.

Instead of asking me for a keyring, nothing.

So I tried to connect and was asked for the whole 26 digit WEP key. Doh!

What I was after was having the system connect to the internet without being prompted (which it was doing already) and without prompting me for a key (which it was).

At the moment (still very new to Ubuntu) when I switch on the machine I don&#8217;t get asked for any passwords. I only get asked when I try to connect to the internet, or install new packages etc.

Thanks, again, for any help.

---

### Post by mcduck on 2009-02-05
Don't delete the keys from the keyring, just the keyring password.

Open the Keyring manager, then go to Edit/Preferences. On the Password Keyrings-tab select the "login"-keyring, and click "Change Unlock Password"-button. Then type your old keyring password but leave the fields for new password empty and click "Change".

---

### Post by Scubdup on 2009-02-05
Awesome, cheers McDuck. Will give this a go as soon as I get home. And thanks to you and Pricechild for humouring a novice with no clue!

I've printed out the free Beginners' Guide so hopefully next time I come back I'll have a slightly better idea of what I'm doing.

---

### Post by Scubdup on 2009-02-07
> **mcduck said:**
> Don't delete the keys from the keyring, just the keyring password.

Open the Keyring manager, then go to Edit/Preferences. On the Password Keyrings-tab select the "login"-keyring, and click "Change Unlock Password"-button. Then type your old keyring password but leave the fields for new password empty and click "Change".

This worked exactly as needed. Thanks a lot!

---

### Post by GJCT on 2009-04-01
I have tried all the process in the above posts, but when I click on "change" it says access denied. I assume this is because I am using the wrong password, but I have tried the only two passwords I have ever had on ubuntu (I am very new) and neither work. 

Could anyone help with this - I'm out of options!

---

### Post by gandaran on 2009-04-01
> I have tried all the process in the above posts, but when I click on "change" it says access denied. I assume this is because I am using the wrong password, but I have tried the only two passwords I have ever had on ubuntu (I am very new) and neither work.

Could anyone help with this - I'm out of options!
this is easy to set up if you do it correctly, first delete/remove any existing keyring profile, enter you WEP key again when you connect, the next time you are asked to set a keyring password, **don't** enter any, just click okay or choose the unsecured option.

---

### Post by GJCT on 2009-04-12
> **gandaran said:**
> this is easy to set up if you do it correctly, first delete/remove any existing keyring profile, enter you WEP key again when you connect, the next time you are asked to set a keyring password, **don't** enter any, just click okay or choose the unsecured option.

Thanks, this worked - I just deleted my login keyring and then created it again straight away. Connects automatically now.

---

