---
title: "Running Genymotion/MEmu on a proxy"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by prakharsr on 2016-10-16
I am at a place where there is a proxy server along with  username/password authentication. Apps like MEmu/bluestacks/Genymotion cannot run on proxy so i googled  and found some ways to work around this problem - ( before i start i  gotta tell that i use both Windows10 and Linux Mint so any workaround  for my problem for both platforms would be much appreciated)
  
[LIST=1]
[*]using an app which tunnels the whole virtual device through the proxy.
[/LIST]
  -----(a) Proxy Droid - i used this app whith the HTTP authentication  and proxy and it works well with the browser and google play store but  it fails to run some apps like youtube, clashofclans etc.
  -----(b) Psiphon - i generally use this app on my mobile phone and it  works for all of the apps by routing the device through a Socksv5  proxy, BUT it crashes when i run it on on android emulators. Psiphon  connects and simply crashes the whole device in genymotion/MEmu.
  -----(c) Drony - this app is for those who don't have super user  priviliges (or simply a phone without root) . It has the option to force  user-selected apps  to run behind a proxy by linking and passing the  traffic through ORBOT, sadly my internet provider has blocked Tor's  services and it fails to connect . ( the browser and google play store  work in it but CoC and youtube don't)
  
[LIST=1]
[*]So in google i found posts related to setting proxy using the  advanced options in wifi options, but sadly it works only with the  browser.( [Genymotion proxy with user/password]("http://stackoverflow.com/questions/20996772/genymotion-proxy-with-user-password") )

[*]i also tried using CCproxy and psiphon3.exe to tunnel my whole pc  but it doesn't make MEmu/Bluestacks go through that socksv5 connection.

[*]i have set up my apt.conf file in linux ( alongwith the proxy and  authentication) but it too gives only the terminal and software manager  access to the internet  but fails to do so for Genymotion. i have  manually setup proxy in Genymotion ( again thanks to - [Genymotion proxy with user/password]("http://stackoverflow.com/questions/20996772/genymotion-proxy-with-user-password")).
[/LIST]
  ......... blah-blah
  So ppl help me out please and thanks in advance to anyone who finds a solution XD .
  and p.s - if anyone wants any snapshot / anything else that might  include some work on my part , just tell me so and i'll be ready to help  
  cheers - Prakhar Sharma

---

