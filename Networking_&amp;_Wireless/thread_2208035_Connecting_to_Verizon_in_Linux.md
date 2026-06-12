---
title: "Connecting to Verizon in Linux"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by sighthnd on 2014-02-26
For several years after I got my laptop, I had been able to connect to a router which was able to connect to the internet through the modem provided by Verizon. Then sometime later, the connection through the modem stopped working and the only connection I have been able to establish since then has been using the router function of the modem. Unfortunately, I have only been able to establish that connection in Windows. Initially, I thought that the problem was that the modem/router was set up in WEP and that my linux setup only supported WPA/WPA2. However, I changed the modem/router over to WPA and I still cannot connect in Linux.

Some details of the setup I know:
[LIST]
[*]The modem is actiontec (exact model escapes me at the moment)
[*]Connection from the modem to the internet is by pppoe with username/password same as for logging in to email. This is the same as it was when the connection worked
[/LIST]

What steps can I take to diagnose whether the problem is of connecting to the router (either the standalone one or the one combined with the modem) or of connecting through the router to the modem? Anything else I should test?

---

### Post by varunendra on 2014-02-27
> **sighthnd said:**
> Connection from the modem to the internet is by pppoe **with username/password [COLOR="#FF0000"]same as for logging in to email[/COLOR]**. This is the same as it was when the connection worked

You really shouldn't reveal such information on publicly accessible areas, unless you don't care about that email (and the contacts who are in its address book). If you do, I suggest you edit the post to remove this part of the post and I'll edit mine to remove this quote. Else I'll leave it here as a caution to others who may come across later.

> What steps can I take to diagnose whether the problem is of connecting to the router (either the standalone one or the one combined with the modem) or of connecting through the router to the modem? Anything else I should test?

Let's first take a look at your system level setup. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by kurt18947 on 2014-02-28
Are you certain the 'modem' from Verizon is operating properly?  The lights are behaving as you would expect when powering down and restarting?  You haven't made any changes to your wiring like running a phone line close to and parallel to an AC line?(ask me how I know about that one!:oops:)

---

### Post by sighthnd on 2014-02-28
All the lights are as they should be AND it connects perfectly under Windows.

---

### Post by sighthnd on 2014-02-28
I'll try following the "Wireless Script" when I next get to my setup at home.

> **varunendra said:**
> You really shouldn't reveal such information on publicly accessible areas, unless you don't care about that email (and the contacts who are in its address book). ...

Did you think that I meant that my email username is "username" and my email password is "password"? The intent is that the connection to pppoe uses the same username and password as the email, something anyone using Verizon's DSL service can find out independently. The only way that information could be useful is if someone were to sniff the password when I connect online, in which case anyone doing that could just sniff the password when I connect to the email. Trust me, my actual password has some diabolical features in it.

---

### Post by sighthnd on 2014-02-28
I've run [FONT=courier new]wireless_script[/FONT] and posted the result to pastebin. The URL is [http://pastebin.ubuntu.com/7012693/](http://pastebin.ubuntu.com/7012693/)

Cell 01 in the list of networks is for the standalone I have. Cell 06 is my router/modem combination.

---

### Post by sighthnd on 2014-02-28
Don't know if there was any specific action that did it, but it now connects to the internet. The indicator is that the network from the router/modem is the one that is active.

---

### Post by varunendra on 2014-02-28
Glad it fixed, anyhow.

But if the problem returns again, the first suggestion would be to upgrade to 12.04 LTS (will be supported till April 2017). The next LTS will be released in April this year and will be supported till April 2019.

There are a few other things you can do to try optimizing the connectivity, like setting the encryption to pure WPA2-AES (Cell 01 is using WPA/WPA2 mixed mode, absolutely discouraged, and the Cell 06 is using WPA (1)) and using driver parameter like nohwcrypt=Y, but beyond that, any attempts would make much sense on a currently supported version.

While 10.04 was a very good release, it is outdated now and is no more supported : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by sighthnd on 2014-03-01
Now that it is connected, I can try upgrading. There again, with another computer that I haven't put Linux on yet (just finished backup of win stuff, already downloaded 13.10 image but haven't burned to disk yet) I might just leave that one as is.

As to the networks, I thought that the router for Cell 01 was set to WPA2 exclusively. Could be mistaken, but would have to log in on it. Most likely moot though unless its connection through the modem can be resolved.

The modem/router for Cell 06 does not support WPA2. Don't know anything about the parameters.

---

