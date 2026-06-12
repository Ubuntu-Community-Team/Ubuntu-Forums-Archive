---
title: "Proxy Settings and Command Line"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by vasdjs on 2009-10-12
Hi, I'm trying to teach myself some command line linux on a fresh installation of 9.04 since most roads seem to lead to the command line sooner or later. My trouble is that I use a proxy server at work and when I come home I don't. Terminal seems to remember the proxy settings even although I take them out of Network Proxy and apply system wide. For good measure I also take it out of Firefox, but if I try sudo apt-get upgrade in Terminal, for example, the command line immediately goes to my proxy server and the command fails....
The proxy server details must be stored somewhere, and I should probably be able to change the proxy from the command line!!! Thanks in advnce, vasdjs

---

### Post by PrePenguin on 2009-10-12
Suggest you set - up a home account under another user name so you dont have to edit these settings each time you change locations i am assuming this is a laptop you commute back and forth to work? That what i would do .. I know it would take a little time getting files etc moved around but in long run worth the less frustrastion in my mind.

---

### Post by diesch on 2009-10-12
Most command line program use the environment variable $http_proxy if it is set.

---

### Post by vasdjs on 2009-10-13
Thanks for the suggestions guys - i think I'll set up another account, but still keen to know where Jaunty might keep the rogue proxy setting, becuse I can't get rid of it for Terminal command line work. Any ideas? vasdjs

---

### Post by vasdjs on 2009-10-23
Does anybody know where I can find a good post or guide on proxy settings??? I have been searching the forums for about 2 weeks trying to pull useful info out of different contexts, and a  lot of people ask this same question in their own way. I work in an envirionment with 3 different proxy servers, 1 requires authentication and the other 2 don't. I also use the laptop on my DSL at home with a direct connection. I therfore need to be changing the proxy server 3 or 4 times a day. Jaunty seems to hold on to the original proxy server address so that any attempt to update thru any other server fails. I have tried to amend the http_proxy using various commands without success. There must be a comprehensive how-to somewhere??? vasdjs:confused:

---

### Post by satish.iith on 2010-02-14
it is okay if u r changing it regularly
but i want to change it permanently and i changed it in synaptics and applied system wide but still when try to download files from internet it shows connection failed.
can u help me change my proxy settings in terminal

---

### Post by zacck on 2010-11-12
Well I know this is a lot late but recently I had the same problem in school its a manual proxy setting and my ISP setting is automatic at home so when I got home I couldn't perform updates or installs ... after some frustrations and a couple of re-installs i realized that when changing the proxy settings back to "Direct internet connection "  in System>Preferences>Network Proxy if I cleared the values in the proxy fields then changed to "Direct internet connection" then installs and updates would work try it ........






The devil said "virtue is in the middle " as he sat between two lawyers

---

