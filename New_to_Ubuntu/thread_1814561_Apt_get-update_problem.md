---
title: "Apt get-update problem"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Smaug95swe on 2011-07-29
Okey so this is what happends:

At the top of the screen there is a big "!" that says...

[IMG]http://i.imgur.com/k7T5U.jpg[/IMG]

And when i try to update it dont find any and when i try to do "sudo apt-get update" 

I get this


W: Failed to get [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to get [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

as you can see its called MAIN both of them.. thats why i dont want to disable them... because i have a feeling that they are important... 

Anyone help plz?

---

### Post by mikewhatever on 2011-07-29
It should be safe to disable the PPAs for the sake of updating, especially the ones that exist no longer. If you still have the feeling after updating, re-enable them.

---

### Post by wildmanne39 on 2011-07-29
Hi, I gave you the answer a day ago at this link.
[http://ubuntuforums.org/showthread.php?p=11094226#post11094226](http://ubuntuforums.org/showthread.php?p=11094226#post11094226)

Please be aware it is against forum rules to start two threads on the same subject.
Thank you

---

### Post by Smaug95swe on 2011-07-29
Im sorry about that i was just scared i might some how crash my system if i updated the stuff without updating these cuz these were called Main... Thanks ill try that

---

### Post by Smaug95swe on 2011-07-29
And it looks like it didnt work to disable for some reason hold on a minute

---

### Post by Smaug95swe on 2011-07-29
I got it disabled but its still the same problem :S weird...

Wait a sec might have done abit wrong let me try to fix... sorry my sleeping hasent been so great

---

### Post by evamagunda on 2011-07-29
i cannt play mp3 a plug in is need.i dnt hv internet l m using ubunt 11.04.wat cn l do.i hv downloaded decibel player and vlc bt l dnt knw hw to install.plz its my 1st time using ubuntu

---

### Post by Smaug95swe on 2011-07-29
[http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages) I cant find this one But i think i disabled the right for the source one

---

### Post by wildmanne39 on 2011-07-29
Hi, ok run this again and post the results if it does not work.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by wildmanne39 on 2011-07-29
Hi, evamagunda please start your own thread with a good title describing your problem, your issue is not the same as the OP's.

---

### Post by Smaug95swe on 2011-07-29
W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Misslyckades med att hämta = Failed to get/download... i can tell you what it says when i disable/enable them if u want but its the same thing... dont know why it says that when i disable them tho

---

### Post by wildmanne39 on 2011-07-29
Hi, with them disabled run this two commands.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by mikewhatever on 2011-07-29
> **Smaug95swe said:**
> Im sorry about that i was just scared i might some how crash my system if i updated the stuff without updating these cuz these were called Main... Thanks ill try that

If you are worried about the system stability, I'd advise against adding any external repositories, even with the word 'main' in the URL.

---

### Post by Smaug95swe on 2011-07-29
Those were the Orginal rep if im right... havent added any at all just like canon and such :P (or whatever its called) thats why i was unsure about disable them

And im trying that one above :D updating right now... abit slow tho

---

### Post by wildmanne39 on 2011-07-29
Hi, so that fixed the problem?

---

### Post by Smaug95swe on 2011-07-29
it just got done took over an hour... and no... 
just more errors

W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Misslyckades med att hämta bzip2:/var/lib/apt/lists/partial/se.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources  Hash-kontrollsumman stämmer inte

W: Misslyckades med att hämta bzip2:/var/lib/apt/lists/partial/se.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages  Hash-kontrollsumman stämmer inte

E: Some index files failed to download. They have been ignored, or old ones used instead.



(misslyckades med att hämta still means failed to get/download )

---

### Post by wildmanne39 on 2011-07-29
Hi, that gave more information you had an update that did not complete run this command.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo apt-get update && sudo apt-get upgrade
```
let me know if that clears it up.

---

### Post by Smaug95swe on 2011-07-29
Did it... Back too 2 problems again.... 

W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by bodhi.zazen on 2011-07-29
That package is in Universe

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=+simple-ccsm](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=+simple-ccsm)

Is there some reason you are using that ppa ? If not, remove it from your sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you are using it, find the ppa on launchpad (I could not find it) and make sure your repository sources are correct.

---

### Post by Smaug95swe on 2011-07-30
And how do i delete it? cant find a way sorry for gbeing retarded :/ and im watching korean starcraft live from tv :D

---

### Post by wildmanne39 on 2011-07-30
Hi, in my previous post I told you how to remove it,but I think you had trouble finding it but all ppa's should be listed in synaptic here is a screenshot.

---

### Post by Smaug95swe on 2011-07-30
I know you meant there but i dont know which one to shut off... shutted off one but didnt help anything at all...

[IMG]http://i.imgur.com/hbd0D.png[/IMG]

can you tell me which ones to shut off? (those are all)

---

### Post by wildmanne39 on 2011-07-30
Hi, the two that have ccsm simple in them.

---

### Post by Smaug95swe on 2011-07-30
oh lol didnt see them sorry -.-

---

### Post by Smaug95swe on 2011-07-30
W: GPG-fel: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: Följande signaturer kunde inte verifieras för att den öppna nyckeln inte är tillgänglig: NO_PUBKEY 4DEF31B9A9E345C0

W: GPC-Error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures could not be verified because the open key is not aviable*: NO_PUBKEY 4DEF31B9A9E345C0

Sorry for my so tried... i think i accidently removed ---^ that key before... how do i get it back?

---

### Post by wildmanne39 on 2011-07-30
Hi, no problem that should fix your problem if it does would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Smaug95swe on 2011-07-30
But wait how do i fix this thing that came up? about the O_PUBKEY 4DEF31B9A9E345C0 should i make another thread about that?

---

### Post by geogur on 2011-07-30
had to install apt-get first then did my upgrade .maybe this is the problem

---

### Post by Smaug95swe on 2011-07-30
that didnt help :/

---

### Post by wildmanne39 on 2011-07-30
Hi, wow where did that come from I wonder? Ok you either need to go to that launchpad and get the key from them, I am not sure how to find it, or uncheck them also.

---

### Post by Smaug95swe on 2011-07-31
all i need is to add the NO_PUBKEY 4DEF31B9A9E345C to my trusted downloads again... how do i add that?

---

### Post by wildmanne39 on 2011-07-31
Hi, here is a command to do that I have never used it,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
and replace KEYID with the number shown in the error message.

---

### Post by Smaug95swe on 2011-08-01
Didnt work... says its not a key :S

---

### Post by bodhi.zazen on 2011-08-01
> **Smaug95swe said:**
> Didnt work... says its not a key :S

You have to use the KEY ID, in this case 4DEF31B9A9E345

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

The rest of that page may also be helpful.

---

### Post by wildmanne39 on 2011-08-01
I see you already have the solution thank you bodhi.zazen.

---

### Post by Smaug95swe on 2011-08-11
Hey this didnt work... still says the same problem... Can you please write the exact "code" i should put in the terminal?

---

### Post by bodhi.zazen on 2011-08-11
> **Smaug95swe said:**
> Hey this didnt work... still says the same problem... Can you please write the exact "code" i should put in the terminal?

The code is posted here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by Smaug95swe on 2011-08-17
Still couldnt get it to work... sorry if im some how retarded... tried them all and they only say
 gpg: requesting key A9E345C0 from http server ppa.launchpad.net
and thats not the full key....

---

### Post by Smaug95swe on 2011-08-17
is there somehow you can post the exact code to put in there -.-

---

