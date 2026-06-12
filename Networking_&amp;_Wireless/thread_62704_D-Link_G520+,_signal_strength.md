---
title: "D-Link G520+, signal strength?"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by Varghjärta on 2005-09-05
Howdy!, i'm one of those folk who have been trying to switch from win to the unix world for several years always ending up going back. But I feel I really want to give Ubuntu a shot, it's cleanness feels as though I might even like it _if_ I can get it up and running.

My problem is that I access to the internet only via Wireless accesspoints (i live in a dorm room on a school campus), but it ain't working!

I've googled, rebooted into ubuntu, googled some more and searched these forums and not once did I find what I need :(

The thing is, that appearently, Ubunutu _does_ detect my D-Link wireless card without a hitch, it displays it in the administration/network as not configured. I go in, configure it with the network name and the WEP-key. And when I save it all it pops up this hope-giving progressbar about it trying to connect. And then it closes, and in the control panel it says the network card is "activated" and configured. BUT, I am still unable to connect to any network outside my own computer. No firefox, no nothing works.
With my limited abilities as a ubuntu and linux newb I think Ive managed to find out that i'm not even assigned an IP (the router is supposed to do that, dynamically so I have no static ips to enter that I know of).

After much more searching, I decided to write down every command I run across in threads about d-link and wireless(with intent on trying them randomly and hope one works).. and using "iwconfig" I can see the status of the "wlan0" device.

And appearently if I read the data correctly, it claims the signal strength is incredibly low, every time I redo the cmd it jumps from 6 to as low as 3. While "signal quality" seems to stay at about 33/100.

Now, i'm no expert but my theory is that _that_ is the main reason why I'm not getting throu, not getting an ip and nothing. Might this be a correct assumption?

But here's the _weird_ part, in Windows XP Pro(sp2) that currently is my main OS (hope to change that!) it works perfectly most of the time. Right now the strength is around 80-90% and the quality the same. And I'm downloading stuff.. really fast :) and it generally never goes down to lower then 80%(due to bad weather and such).

Yet when I try ubuntu the strength appears as below 10 all the time and doesn't seem to get any better.

I've even gone about draging the computer(tower) around the room to try and get a better signal(where xp _already_ has one mind you) but with no luck. I do think I manage to raise the signal by a few % but not enough. 

Could someone offer a helping hand?, becouse i'm a newb who would like to give ubuntu a serious go and I know too little of things like these(of unix nature and such) to do something about it myself. And it makes no sense to me that I get different signals in XP and Ubuntu (?!?).

Any help would be appreciated!.

---

