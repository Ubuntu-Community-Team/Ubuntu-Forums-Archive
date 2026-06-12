---
title: "firefox doesnot work"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by oaridus on 2010-11-05
Hi, I am using Ubuntu Lucid and I am trying to connect to the internet. The firefox and thunderbird both don't work although I have checked that the internet is working fine. I am able to ping and also browse using epiphany browser. please let me know how to fix firefox and thunderbird.

---

### Post by Verbeck on 2010-11-05
try renaming the .mozilla folder in your home folder to something like .mozilla(backup)

---

### Post by ivanovnegro on 2010-11-05
I am not sure but maybe you could reinstall Firefox and Thunderbird.

---

### Post by oaridus on 2010-11-06
I tried doing that but it does not work. help please.

> **ivanovnegro said:**
> I am not sure but maybe you could reinstall Firefox and Thunderbird.

---

### Post by oaridus on 2010-11-06
I searched the net and got this solution

--------------------------------------------------------------
"The following works for me....... Open your Firefox and type about:config at URL address bar and hit enter. U will get a list of lines. Search for the lines given below( simply copy & paste in search bar. Eg-paste'network.http.pipelining'). Make the following changes. To make a False into True, select the line to change, and double click. On the 2nd option change, right click and select Modify

- network.http.pipelining > Make it True

- network.http.pipelining.maxrequests > Make it 8 or 10

- network.http.proxy.pipelining > Make it True

- network.dns.disableIPv6 > Make it True

I hope this helps for some users"

-------------------------------------------------------------

I tried doing this and the firefox now works. But I don't know how to fix thunderbird. please help

---

### Post by Crusty Old Fart on 2010-11-06
Howdy oaridus:

Thunderbird can be a little tricky. It wants to default to setting up IMAP accounts. While there's nothing wrong with that, there's a trick you have to perform to get it to set up a POP account.

Here's a link that might help:
[Creating accounts in Thunderbird for popular email providers]("http://kb.mozillazine.org/Creating_accounts_in_Thunderbird_for_popular_email_providers")

If the information they have doesn't help, please post back here with the type of account you're trying to create (either IMAP or POP) and who your email provider is.

---

