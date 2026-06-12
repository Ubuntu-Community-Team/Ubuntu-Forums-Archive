---
title: "[SOLVED] Hospital Wi-fi Access Problem"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by iheartubuntu on 2008-05-24
My mom is in the hospital right now and I installed Ubuntu on my sisters computer and she brought it to the hospital since they offer free wifi access.

Im having a problem getting my sisters computer to connect.

We see 3 wifi networks with Ubuntu:

SH_Guest
SH_FrontDesk
SH_Nurses

Calling the front desk for the log-in info they told me to use "VIS425" as the username and "guest" as the password. But with Ubuntu, I dont have the option to put in a user name. Well, technically I do if I change the network manager settings. I tried briefly but could not log on.

The front desk also told me to log into the "SH_DeskNetwork" network, which I dont see in network manager, just the three I listed above.

Sometimes when accessing a free wifi spot a webpage will come up to input name/password... such as when I used my Ubuntu system in a hotel once without a problem at all. At the hospital, I dont get anything of the sort.

So, in trying to piece together what the front desk told me to do and with what I see available to me.. I tried logging into the "SH_Guest" wifi network, then typing "guest" as the passphrase. It didnt work, but it showed 95% antenna signal anyways.

Here is the error message we get when trying to view a webpage:
> 
Secure Connection Failed

1.1.1.1 Uses an invalid security certificate.

The certificate is not trusted because it is self signed.

(Error Code: sec_error_ca_cert_invalid)

I also see any site I try to view is redirected with something like this (with the error message above as the webpage):

[https://1.1.1.1/login.html?redirect=http://www.cnn.com/](https://1.1.1.1/login.html?redirect=http://www.cnn.com/)

(that may not be exact but I think its close)

Any help with this would be greatly appreciated! My mom is battling lung cancer, had a stroke, and now broke her hip last week so she is going to be there another couple weeks. My sister wants to stay during the day with mom so it would be nice if she could log into their system.

Ahh, yes.. forgot to mention... maybe network manager is a problem? Could I try any other network managers in the repositories? Any recommendations? Thanx

---

### Post by superprash2003 on 2008-05-24
since its a free network.. i dont think you need to enter any passphrase..Just enter the network name without any password..The username and password could be asked when you try to access a site .. or maybe they use a proxy..i think its mostly an open network and you just need to enter network name to join the network..
  Really Hope that your mom gets well soon!!!Take Care..

---

### Post by iheartubuntu on 2008-05-24
Do I just click on the "SH_Guest" wifi without any passphrase and log onto it?

Or should I try to type in "SH_DeskNetwork" that they told me to use (which I dont see).

I wonder why they gave me a user name & password then. Ive never had this sort of problem with a free network.

And since I couldnt see the "SH_DeskNetwork", do you think its hidden? I would think that would pose problems for a lot of users if it was hidden.

---

### Post by superprash2003 on 2008-05-24
some people do that on purpose.. you can hide it such that it wont show in the network list.. try connecting without any passphrase .. it should login

---

### Post by iheartubuntu on 2008-05-25
I went back to try it out and no go. It just keeps pulling up a redirect page with that 401 style error message.

I tried logging in with no password on the SH_Guest and then I tried the same with SH_DeskNetwork which might have been hidden and get nothing. I wonder if my sister screwed it up somehow :) she is pretty good and screwing things up :) I might bring in my laptop to see if I can log into the system without a problem. Its frustrating because I have one brother who keeps saying "its your stupid Ubuntu". And I can only say for now that Ive never had this problem on other free networks, but at least Im not getting viruses every week like he does. Not much of a come back :)

Is there any way to delete or edit the networks in case my sister entered some password? Maybe I can clear it so we can start from scratch.

---

### Post by Ayuthia on 2008-05-25
Have you tried connecting to SH_Guest and going to this page:
[https://1.1.1.1/login.html](https://1.1.1.1/login.html)

From what I can tell, it looks like there is a web page that you need to go to and enter the username and password information before it gives you access.

---

### Post by iheartubuntu on 2008-05-25
> **Ayuthia said:**
> Have you tried connecting to SH_Guest and going to this page:
[https://1.1.1.1/login.html](https://1.1.1.1/login.html)

From what I can tell, it looks like there is a web page that you need to go to and enter the username and password information before it gives you access.

I was thinking the same thing but it came up with nothing.

---

### Post by iheartubuntu on 2008-05-26
Problem solved. I was looking around on the redirect error page that said:

> Secure Connection Failed

1.1.1.1 Uses an invalid security certificate.

The certificate is not trusted because it is self signed.

(Error Code: sec_error_ca_cert_invalid)  

Well, I missed the little line at the bottom of the page that was clickable and said "Other options?" My sister clicked it and was taken to the login page.

---

