---
title: "configure empathy"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by alaukik.kot on 2009-08-15
hi, i have recently downloaded empathy from synaptic and also other supporting softwares along with it
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

but i'm unable to connect, my computer is connected with huge lan of my college, which is then connected to INTERNET via server( whose ip 172.31.16.10) pidgin use to work very fine with me....
 can i configure my empathy, will it work... can some one please guide me... i'm really interested in starting google voice on my ubuntu...

---

### Post by alexlafreniere on 2009-08-15
Try going into connection settings and configuring it to work with what sounds like your school's proxy server. I've never used Empathy but this sounds like it's the problem.

---

### Post by alaukik.kot on 2009-08-15
hi:)
 there is no option for separate connection settings in empathy, as it is in pidgin...

---

### Post by ubuntu27 on 2009-08-15
It might be a bug that is present in the old version of Empathy.

Get the new version by adding [PPA for Telepathy]("https://launchpad.net/~telepathy/+archive/ppa"):

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)


Here are the instructions. I assume you are using the latest Ubuntu 9.04 (Jaunty):


1) Open _Software Sources_, located at System menu/Administration/Software Sources

2) Go to the _Third Party Software_ tab.

3) Click on Add button.

3) Copy the following:

```
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu jaunty main 
```

4) Click on Add Source.

5) Click on Add button again and copy:

```
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu jaunty main
```

6) Click on Add Source.

7) Close it, and Reload the repositories.



Now we are going to add the Signing Key for Telepathy's PPA. 

1) Go to [PPA for Telepathy]("https://launchpad.net/~telepathy/+archive/ppa") site

2) Click on the link next to the thext "Signing Key". In this case it is "[1024R/FA3A1271]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271&op=index")"

3) Click on 1024R/[FA3A1271]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x638ABCA0FA3A1271")

4) Copy ALL the text from "-----BEGIN PGP PUBLIC KEY BLOCK-----" to "-----END PGP PUBLIC KEY BLOCK-----"

5) Paste to an Text Editor.

6) Save it with an extension "key".  Example: telepathy.key

7) Open SOftware Sources.

8) Go to _Authentication_ Tab

9) Click on "Import Key File..."

10) Open or select the recently saved  key file.

11) Close SOftware Sources



Now upgrade Empathy.

---

### Post by alaukik.kot on 2009-08-15
hey thankx ton
but link for that singning key  "http://keyserver.ubuntu.com:11371/pks/lookup?search=0x71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271&op=index" i tried opening but i faced an error called the requested url could not be retrieved.... 
help can you pl paste here matter between

 "-----BEGIN PGP PUBLIC KEY BLOCK-----" to "-----END PGP PUBLIC KEY BLOCK-----"

thankx a lot :)
waiting for your reply

---

### Post by alaukik.kot on 2009-08-15
i'm still not able to open that link... please help...
waiting for reply

---

### Post by SoftwareExplorer on 2009-08-15
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXOsIgEEAO8CYq92PrPZgXxuCsvsjTwzdfGOVpKBbjNGBTA4PgMTnowIYQUDKPCuPYBt
O1dNbupzGb/ko3x1630kQo4htUV7uiy2d2l6NPgFXdw0K3mAbqKgVoHzxHaFqDG1qFbueBi9
+EgW/91g4Me4u6dtLnHwus9tpiVlHrZihUnaTXMfABEBAAG0G0xhdW5jaHBhZCBQUEEgZm9y
IFRlbGVwYXRoeYi2BBMBAgAgBQJJc6wiAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ
Y4q8oPo6EnE0XwQA5G6nn/ABqgoD2EXBW/0zdp7+5YxK5PKEmi2lL1DDHQJ1bm/KUr1UDW0V
5V4n4g7eXK2K7vnIEB/bL5jDsLV1XvrV1uVCH2jgSpHrNvMhSU5qeAwH+3s5ZtlHgBVb1pgU
QvR8R5/oy1Ta0PajHsisbzpsfr9AQeFgQlqZvxdTCjs=
=XJj0
-----END PGP PUBLIC KEY BLOCK-----
```

---

### Post by ubuntu27 on 2009-08-15
> **alaukik.kot said:**
> i'm still not able to open that link... please help...
waiting for reply

SoftwareExplorer answered it ^^.

Open a text editor like Gedit [Application menu/Accessories/Text Editor]
and copy and paste

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXOsIgEEAO8CYq92PrPZgXxuCsvsjTwzdfGOVpKBbjNGBTA4PgMTnowIYQUDKPCuPYBt
O1dNbupzGb/ko3x1630kQo4htUV7uiy2d2l6NPgFXdw0K3mAbqKgVoHzxHaFqDG1qFbueBi9
+EgW/91g4Me4u6dtLnHwus9tpiVlHrZihUnaTXMfABEBAAG0G0xhdW5jaHBhZCBQUEEgZm9y
IFRlbGVwYXRoeYi2BBMBAgAgBQJJc6wiAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ
Y4q8oPo6EnE0XwQA5G6nn/ABqgoD2EXBW/0zdp7+5YxK5PKEmi2lL1DDHQJ1bm/KUr1UDW0V
5V4n4g7eXK2K7vnIEB/bL5jDsLV1XvrV1uVCH2jgSpHrNvMhSU5qeAwH+3s5ZtlHgBVb1pgU
QvR8R5/oy1Ta0PajHsisbzpsfr9AQeFgQlqZvxdTCjs=
=XJj0
-----END PGP PUBLIC KEY BLOCK-----

```

and save it with name.key

---

### Post by alaukik.kot on 2009-08-17
"ENTER PASSWARD FOR DEFAULT KEYRING TO UNLOCK"
 this is new message i receive when ever i start empathy, i choose option as "DENY" emathy dose starts but doesn't really connect to internet or fails in showing my buddy list and always in attempt of connecting. never actually gets connected

---

### Post by alaukik.kot on 2009-08-20
"ENTER PASSWARD FOR DEFAULT KEYRING TO UNLOCK"
this message is repeatedly coming on my screen as i start EMPATHY, 
pl help me out of this

---

### Post by ubuntu27 on 2009-08-21
> **alaukik.kot said:**
> "ENTER PASSWARD FOR DEFAULT KEYRING TO UNLOCK"
this message is repeatedly coming on my screen as i start EMPATHY, 
pl help me out of this

Click on Allow next time you execute Empathy.
And dosn't it have the option to remember it?  Something like "Allow it forrever" or "allow it for this application"

---

### Post by alaukik.kot on 2009-08-21
Hi:)
 no there aren't any other options then "ok" or "deny". 
i also did complete removal and then again installed the whole thing again.
but still couldn't get rid of this error..
 i'm kindly seeking to fix this up... google voice chat is one of the highly needed utility. 
thank you. waiting for your reply, solution :)

---

### Post by alaukik.kot on 2009-08-22
i tried various options to get rid of this error, it is just out of my reach. please help me out....

---

### Post by alaukik.kot on 2009-09-05
hey finally my empathy started working fine, i repaired all broken packages in recovery mode and it started working...
  then i imported my account settings from pidgin, as there was an option available there, but now i can't access voice chat of gtalk, audio chat button isn't hyperlinked. how to go about getting my empathy start supporting voice chat too, i can comfortably do chat using text in empathy but not voice chat

please help...

---

### Post by ubuntu27 on 2009-09-05
Sorry, I can't help you there as I did not experience those problems.


I recommend you to create a **new thread** and describe the new problem. People pay more attention to new threads since it means that no help was offered yet. 


Also, you might want to ask for help at [LinuxQuestions.org]("http://www.linuxquestions.org/") also.

---

