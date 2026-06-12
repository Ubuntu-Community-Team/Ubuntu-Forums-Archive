---
title: "Aircrack-ng Suite: WPA PSK dictionary attack"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by flaflatas on 2009-04-16
Hello all!

I am a relatively new user of Linux and I am trying to figure out how aircrack-ng is working. I am trying to get into a WPA protected network. I have already the four way handshake. I tried with two different dictionaries to get the passphrase, but in vain.

My questions are the following: 
[LIST=1]
[*]Does the passphrase need to be EXACTLY as is in the dictionary? i.e.if the passphrase is "stoomach", does it also need be EXACTLY the same in the dictionary?
[*]Is there a necessity for the dictionary to include words written in the language of the  passphrase? i.e. if the passphrase is a polish word, do I need to use a polish dictionary for the attack?
[*]Any suggestions, where could I get "rich" dictionaries?
[*]Are there programs that could find the passphrase by checking on an online dictionary?
[/LIST]

There you go! Many questions on this issue...

Thank you very much in advance

[COLOR="Red"][B]PS. The WPA protected network I am referring is MY WPA protected network. 
    No ILLEGAL activity! This post is only intending to give me the
    knowledge to avoid my network being compromised.[/B][/COLOR]

---

### Post by nandemonai on 2009-04-16
> **flaflatas said:**
> Hello all!

I am a relatively new user of Linux and I am trying to figure out how aircrack-ng is working. I am trying to get into a WPA protected network. I have already the four way handshake. I tried with two different dictionaries to get the passphrase, but in vain.

I hope 'a WPA protected network' means _your_ WPA protected network.

---

### Post by subzero316 on 2009-04-16
1) Yea the word must be exactly the same.

2) Well if the word is in polish dict then use one. If french then used a french dict.

3) Get a Dict from here [http://www.openwall.com/wordlists/](http://www.openwall.com/wordlists/)

4) Online ...No that's just stupid cause it'll take more time to crack. if it keeps looking online.



PS: Experiment On your own Network.

---

### Post by gali98 on 2009-04-16
Trying to break into someone else's network without their permission is almost always illegal. Please do not ask questions about illegal activities.
Kory

---

### Post by flaflatas on 2009-04-16
> **subzero316 said:**
> 1) Yea the word must be exactly the same.

2) Well if the word is in polish dict then use one. If french then used a french dict.

3) Get a Dict from here [http://www.openwall.com/wordlists/](http://www.openwall.com/wordlists/)

4) Online ...No that's just stupid cause it'll take more time to crack. if it keeps looking online.



PS: Experiment On your own Network.

Thank you very much for your answers!!!
So, according to these answers, a passphrase with no meaning at all, in alphanumerical form, is practically impossible to crack (at least under the present circumstances)

---

### Post by lemmy999 on 2009-04-16
Seeing as the network is yours then its pretty easy to check whether the passphrase in your dictionary needs to be "exactly" the same as your password. Simply compile a list of all the possible ways ( uppercase/lowercase/spaces/underscores etc) that YOUR password could be written and check that list against the real password.

---

### Post by flaflatas on 2009-04-17
> **lemmy999 said:**
> Seeing as the network is yours then its pretty easy to check whether the passphrase in your dictionary needs to be "exactly" the same as your password. Simply compile a list of all the possible ways ( uppercase/lowercase/spaces/underscores etc) that YOUR password could be written and check that list against the real password.



Thank you very much for the suggestion! I was using the password.lst of aircrack-ng for my network's tests.

---

### Post by Paqman on 2009-04-17
> **flaflatas said:**
> Thank you very much for your answers!!!
So, according to these answers, a passphrase with no meaning at all, in alphanumerical form, is practically impossible to crack (at least under the present circumstances)

For WPA, yes. For WEP, no.

---

### Post by flaflatas on 2009-04-17
> **Paqman said:**
> For WPA, yes. For WEP, no.

Dearest friend, 
I was only asking for the WPA protection. Since WEP password is found through statistical analysis, it is normal that no matter how insane the password might be, it is going to be found. My inquiry was only regarding WPA: password and its relation to a dictionary.

Cheers!

---

### Post by gali98 on 2009-04-17
Didn't mean to accuse. Just wanted to make sure :)
Have Fun!
Kory

---

### Post by flaflatas on 2009-04-20
> **gali98 said:**
> Didn't mean to accuse. Just wanted to make sure :)
Have Fun!
Kory

My apologies...

But I had a bad start in Ubuntu Forums. I found myself awarded with an Infraction and being on the defence position, trying to explain that the network is mine and that my motivation is pure...

---

