---
title: "What is the difference between install, setup and configure ?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by myselfmani on 2011-04-12
Actually, I need to understand the general basic concepts for these three (install, setup and configure) to install any software. For example,
What is software configuration?

---

### Post by uRock on 2011-04-12
Hello and welcome to the forums,

What kind of software are you trying to install? 

What file type is it?

Cheers,
uRock

---

### Post by HermanAB on 2011-04-12
It is very similar to "Abort, Retry or Fail?"

Sorry, I just could not resist it...

---

### Post by wep940 on 2011-04-12
Jeez - I thought it was a horse, a duck and a table!  ;)
 
Seriously, we do need to know a particular example you would like to work with - some things are usually pretty standard, but there are things that are not.  One can never know until the example being used is presented.

---

### Post by profeta81 on 2011-04-12
Usually configure means either to change the settings of an application already installed on the system to suit the user preferences or to prepare an uninstalled application for compilation and installation by determining few of your system specification (what is the default compiler, whether a particular dependency is installed, needed header files and-or libraries, cpu type, RAM, etc).

install means to move the files (binaries, libraries, headers, configuration files, documentation, etc) needed to run an application in the proper directories and possibly change files attributes. GNU/Linux software is usually installed via the following process:

```
configure -> compile -> install
```

setup is an ms windows specific terminology that essentially has the same meaning of install, the essential difference being that setup is usually a blacked out process during which the user doesn't really know what's going on in his system (often a reassuring progress bar is also shown).

---

### Post by oklokl on 2011-04-12
Ubuntu 10.10 Maverick Meerkat                                                                                      
ex> [https://launchpad.net/~stebalien/+archive/simple-service-manager]("https://launchpad.net/%7Estebalien/+archive/simple-service-manager")                                                     **simple-service-manager    **


This PPA can be added to your system manually by copying              the lines below and adding them to your system's software              sources.

deb [http://ppa.launchpad.net/stebalien/simple-service-manager/ubuntu](http://ppa.launchpad.net/stebalien/simple-service-manager/ubuntu) karmic main 

Signing key:
[COLOR=Red]
-----BEGIN PGP PUBLIC KEY BLOCK----- [/COLOR]Version: SKS 1.0.10  mI0ESXW3KQEEAK9jVMeIeuPjez5qyD6pDKNM8anukLGT1WaHr/SCUo1HdWByOgOAl88U/9Ts IvxccGicN6hFWuk7DF1OPhyzkSd8Mfe0wFbTJ9GMh+NDY6YUPoGw1fjZeD+VLytUDpgGmDUt AhrGzt9doXZI1Xpl7prPLUB4VPKYJQ8tLRa6eLQZABEBAAG0G0xhdW5jaHBhZCBQUEEgZm9y IHN0ZWJhbGllboi2BBMBAgAgBQJJdbcpAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ v8e7kI/CdXUNvgP7BoqQudjdTOOLFVnl9s1hBRIDRxV6snTW7jz2DV0S/6lJtJXRt24Qf1aw U3xKEgTSWrkLf5xhXfdq29O8aCVXxnP4qDS2wk0TmbY35MPF6G0D9tilCDDoqIf1iq9yoE2p Eby12jhsNMGomNDU1pdphOggBS9fUn4Bel7/GGRoNeo= =FOWK[COLOR=Red] -----END PGP PUBLIC KEY BLOCK-----[/COLOR]

copy Ctrl+C
[COLOR=Red]-----BEGIN PGP PUBLIC KEY BLOCK----- 
[/COLOR]......
.......
[COLOR=Red] ----END PGP PUBLIC KEY BLOCK----- [/COLOR]
Until here

Signing
mouse + The right side

[COLOR=#000000][FONT=Verdana]sudo apt-get update[/FONT][/COLOR]

configure-> find 
[COLOR=Red]simple-service-manager[/COLOR]


[COLOR=#000000][FONT=Verdana]sudo apt-get install test(name program)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo apt-get remove test[/FONT][/COLOR][COLOR=#000000][FONT=Verdana](name program)[/FONT][/COLOR]

error-> [COLOR=#000000][FONT=Verdana]
sudo apt-get install -f[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
ex>
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get upgrade[/FONT][/COLOR]

apt-get --help

or
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Ubuntu ->**setup**

---

### Post by myselfmani on 2011-04-12
Thank you very much, I am waiting for this type of content, but I need more data regarding this topics, can you please give any links or books to know more about this with some examples

---

### Post by myselfmani on 2011-04-12
@profeta81 Thank you very much, I am waiting for this type of content, but I need more data regarding this topics, can you please give any links or books to know more about this with some examples?

---

### Post by profeta81 on 2011-04-12
As others have pointed out already (sarcastically), it's not very clear what exactly you're looking for since software installation is a rather broad topic; and also your question is rather out of place giving that this is a forum about Ubuntu (as the name is meant to suggest).

Anyway here's a howto on building GNU/Linux software from sources:

[http://tldp.org/HOWTO/Software-Building-HOWTO.html](http://tldp.org/HOWTO/Software-Building-HOWTO.html)

and perhaps you may be interested in the wikipedia pages about package managers and installation (slightly windows biased the latter):

[http://en.wikipedia.org/wiki/Package_management_system](http://en.wikipedia.org/wiki/Package_management_system)
[http://en.wikipedia.org/wiki/Installation_%28computer_programs%29](http://en.wikipedia.org/wiki/Installation_%28computer_programs%29)

hope this is useful...

---

