---
title: "Help Configuring Wireless For School Network"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by groberts1980 on 2006-09-01
I need help configuring my laptop to access the wireless network at UWF, where I go to school. They don't use regular wep or wpa keys, it uses our student logins somehow.

Here are instructions on setting it up in XP/OSX:
[http://portal.knowledgebase.net/display/2n/kb/article.asp?aid=133406&n=8&s=]("http://portal.knowledgebase.net/display/2n/kb/article.asp?aid=133406&n=8&s=")

If anybody could take a look at those instuctions and help me port them to Ubuntu, I would be very appreciative.

---

### Post by wjp.reg on 2006-09-01
> **groberts1980 said:**
> I need help configuring my laptop to access the wireless network at UWF, where I go to school. They don't use regular wep or wpa keys, it uses our student logins somehow.

Here are instructions on setting it up in XP/OSX:
[http://portal.knowledgebase.net/display/2n/kb/article.asp?aid=133406&n=8&s=]("http://portal.knowledgebase.net/display/2n/kb/article.asp?aid=133406&n=8&s=")

If anybody could take a look at those instuctions and help me port them to Ubuntu, I would be very appreciative.

Your link gives and error so can't see the instructions.  Better check it and repost.

---

### Post by groberts1980 on 2006-09-06
Sorry about that, try this one:
[http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133406&r=0.2268488]("http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133406&r=0.2268488")

Someone posted about using wpasupplicant, but I'm not sure. They posted this for their wpa_supplicant.conf file:

```

ctrl_interface-/var/run/wpa_supplicant

network = {
   ssid="uwf-argo-air"
   scan_ssid=1
   key_mgmt-WPA-EAP
   eap=PEAP
   group=TKIP
   pairwise=TKIP
   identity="user"
   password="password"
   phase1="peaplabel=1"
   phase2="auth=MSCHAPV2"
}

```

I set that up, but I'm not sure how to run the program to see if its working. I normally use Network Manager at home, but I just connect to regular wireless networks. The one at school uses our school login/pw and PEAP/MSCHAPV2.

---

### Post by randomnumber on 2006-11-29
I am using 6.06 on my laptop now and I am able to always able connect to UWF wireless connection. I plan to upgrade after the semester ends. Please try the following settings in network manager:

Network Name:           uwf-argo-air
Wireless Security:      WPA Enterprise
EAP Method:             PEAP
Key Type:               DyNamic WEP  (Automatic does NOT work!!!)
Identity:               (Sail Lab ID ex. ccc#)
Password:               (Sail Lab Password)

--Default all other options ---

If this does not work check with IT and make sure there is not a problem with your account.

Please inform me if this works for you as I would like to submit a instruction to IT.

---

