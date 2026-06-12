---
title: "Firewalls"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by gumstool on 2009-11-22
Do I need a firewall , and if so what do other users recommend ?

---

### Post by Prodigal Son on 2009-11-22
You already have one - iptables. As far as I know ( haven't found a better alternative ), [ufw]("http://ubuntuforums.org/showthread.php?t=823741") is the easiest way to configure it properly.

---

### Post by phillw on 2009-11-22
> **gumstool said:**
> Do I need a firewall , and if so what do other users recommend ?

Ubuntu (and other linuxes) all come fully firewalled.  You only need firewall tools if you plan on turning some of it OFF.  For general usage, e.g. browsing etc - leave your system as it is.

Regards,

Phill.

---

### Post by gumstool on 2009-11-22
ok cheers . I followed the link but I am really new to Ubuntu , where do I input the code thats specified ?

---

### Post by Prodigal Son on 2009-11-22
> **gumstool said:**
> ok cheers . I followed the link but I am really new to Ubuntu , where do I input the code thats specified ?

In Terminal or Konsole ( depending on whether you use Gnome or KDE ).

---

### Post by phillw on 2009-11-22
> **gumstool said:**
> ok cheers . I followed the link but I am really new to Ubuntu , where do I input the code thats specified ?


I repeat .. Unless you are planning on setting up a file / web / mail server - Leave the default (fully firewalled) in place. Don't alter anything !!!!

If you'd like to learn about firewalls head here ---> [https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

the community wiki for ufw is over here --> [https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw)

Regards,

Phill.

---

### Post by frank002 on 2009-11-22
The Ubuntu firewall is UFW (Uncomplicated Firewall). It should come enabled already. To check open a terminal and type " sudo ufw status" without quotation marks. You are then prompted for your password. Type your password and it should tell you the status of  UFW. If for any reason it is disabled, type "ufw enable", again, without quotations. That is all.

---

### Post by Prodigal Son on 2009-11-22
> **frank002 said:**
> The Ubuntu firewall is UFW (Uncomplicated Firewall). It should come enabled already. To check open a terminal and type " sudo ufw status" without quotation marks. You are then prompted for your password. Type your password and it should tell you the status of  UFW. If for any reason it is disabled, type "ufw enable", again, without quotations. That is all.

By default ufw is disabled.

---

### Post by gumstool on 2009-11-22
THanks for your replies chaps , this is really interesting and I'm learning lots. Anyway my UFW is disabled but to enable it I need to be "root" . can anybody explain how I become root ?? And apologies in advance for the stupid question , I'm off to buy a book on LINUX tomorrow.

---

### Post by gumstool on 2009-11-22
Looked up the sudo command on the UBuntu wiki and understand now what's going on . Cheers for your help anyway and the firweall is enabled.

---

### Post by lisati on 2009-11-22
> **Prodigal Son said:**
> By default ufw is disabled.

Thanks. Enabled on my machine now. 
BTW, many routers come with with firewall capabilities which can be of some help protecting ALL the machines attached to them. (<aside>I have two routers in my home network, mostly out of convenience from a wiring perspective, rather than a need to hook up a lot of machines.</aside>)

---

### Post by Prodigal Son on 2009-11-23
> **lisati said:**
> Thanks. Enabled on my machine now. 
BTW, many routers come with with firewall capabilities which can be of some help protecting ALL the machines attached to them. (<aside>I have two routers in my home network, mostly out of convenience from a wiring perspective, rather than a need to hook up a lot of machines.</aside>)

True. I didn't knew about ufw ( well, I knew that it exists but didn't had the will to enable and use it ) until this summer when I moved and switched ISP's ( from modem and router to a cable ) :)

---

### Post by nitstorm on 2009-11-23
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

found this basic command sheet very useful.. i enabled the firewall and gave vuze an unblocked port wit it... 

hope this post was useful, otherwise, sorry ..

cheers!

---

### Post by mörgæs on 2009-11-23
> **gumstool said:**
> I'm off to buy a book on LINUX tomorrow.

There are also plenty of good books on the web, for example
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by 3rdalbum on 2009-11-23
The default install of Ubuntu does not listen to any incoming connections, therefore it doesn't have an activated firewall.

You only need a personal firewall if you are going to run software on your system that can listen to incoming remote connections, but you don't want it to. The use case for this is very limited; I can't really think of many examples.

If you're not going to run any server software on Ubuntu, then you don't need a firewall; your computer will already ignore 100% of all incoming connections. A firewall is not going to make your computer ignore MORE than 100% of incoming connections, is it? It's like walking into a bomb-proof shelter, wearing a suit of armour - the explosions won't affect anyone inside the shelter, so there's no benefit to wearing the armour. And those suits just make it more difficult to move.

On Windows, you need a firewall turned on and blocking everything from the get-go, because by default Windows does listen to incoming remote connections, and you want to stop this happening.

If your broadband modem/router contains a firewall as well, then it will protect your whole network. You also won't need a personal firewall in that case; packets will be stopped at the router's firewall, so your personal firewall will never actually see any incoming connections unless they come from your own network.

---

### Post by telovin on 2009-11-23
I am new and had recently installed ubuntu 9.10. Thought firewall is automatically configured. Very useful thread. Just enabled my firewall by configuring ufw.. Thanks a lot everyone

---

### Post by BaBz:) on 2009-11-24
this thread is a lot of help to me but i havent gotten very far.
 
this almost could have been a new topic... but i think its along the same lines :)
 
...so i have found the terminal. i have entered 'man ufw' and all of these suggestions showed. i copied and pasted each of them with no result other than the command was not recognised.
from there i went to here and started looking for some help. i saw all sorts of great code to change the iptables or firewalls to allow me to use my browser. i cant access the internet from my ubuntu. i have to switch back and forth from vista to get a tip and try it out.
i cant paste code after restarting :( after hand writing over half a page of it, i gave up and looked to the #ubuntu for help with no luck. so here goes, really basic...
 
i can connect to the internet (after mush torment) but firefox says its unable and for me to check that my firewall allows it. so, what do i type to make it so that i can use the browser while in ubuntu so i can get to understand it better. 
 
it is nothing like windows or anything i would have typed in command to play with windows. i see a lot of helpful stuff on here. much nicer than the MSDN forums . id like to try it.
 
i really want to learn it. i hear its far better and that i would like it. (yeaa!)
 
any tips are greatly appreciated and not a waste of your time :) i know you may have laughed at my question. think of how i will smile when i get your reply :D
 
babz
(my first post on this forum)

---

### Post by bodhi.zazen on 2009-11-24
Interesting you should ask ...

See :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

And this may also help :

[GUFW (gui)]("http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/")

[UFW - Desktops]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/")

[UFW - Servers]("http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/")

---

### Post by 3rdalbum on 2009-11-24
> **BaBz:) said:**
> i can connect to the internet (after mush torment) but firefox says its unable and for me to check that my firewall allows it. so, what do i type to make it so that i can use the browser while in ubuntu so i can get to understand it better.

By default, Ubuntu's firewall is not configured, so all incoming and outgoing connections are allowed through.

Firewalling is not your problem.

I'd suggest checking your connection settings in Network Manager, specifically that it has determined the correct "gateway" and "DNS" addresses. (Right-click the Network Manager and go to Connection Information and check that this is the same as on Windows).

If you need to modify some things - so go to Edit Connections in Network Manager, select the connection, hit Edit, go to IPv4 Settings and change it to "manual". Enter the correct information manually.

---

### Post by BaBz:) on 2009-11-27
oooOOOoo its online! im using it right now! :) 
 thanks to the persons who told me where to find terminal and the suggestions about ufw. 
 i think the real problem is just me turning into 'mush' after too much coffee and frustration. i dont know how it worked though, that will bug me.

 all the terms are different, i have no clue what the commands are.
is there a place where i can find some? ( example: UFW = uncomplicated firewall ) or does that matter? are they even called commands in this terminal?
  im self taught as many people are so i appreciate any help i get. so does this computer.... as it slowly turns into a beautiful machine :):KS
 once i figure that out i will completely remove vista. windows 7 was like cyber hemaroids but, it did encourage me to try ubuntu.

 it looks really really cool. :D thanks

---

### Post by BaBz:) on 2009-11-27
> **3rdalbum said:**
> By default, Ubuntu's firewall is not configured, so all incoming and outgoing connections are allowed through.

Firewalling is not your problem.

I'd suggest checking your connection settings in Network Manager, specifically that it has determined the correct "gateway" and "DNS" addresses. (Right-click the Network Manager and go to Connection Information and check that this is the same as on Windows).

If you need to modify some things - so go to Edit Connections in Network Manager, select the connection, hit Edit, go to IPv4 Settings and change it to "manual". Enter the correct information manually.


 i dont know what caused it really, the night before it wouldnt connect, next day.. no browsing. im just really new. im writing down your suggestion in case it happens again. thanks agian.

---

### Post by 3rdalbum on 2009-11-27
> **BaBz:) said:**
> all the terms are different, i have no clue what the commands are.
is there a place where i can find some? ( example: UFW = uncomplicated firewall ) or does that matter? are they even called commands in this terminal?

They are called commands, but the commands are actually also programs. For instance, when you type "ls" to see the contents of a folder... ls is a program!

If you want to learn more about a specific command, just ask for the "man" (manual):

man ls
man ufw

It will give usage information - basically, how to use the command. Anything in square brackets is optional. Anything in triangular brackets is required. The pipe | says "or" - so if you see this line in the manual:

```
ufw [--dry-run] default allow|deny|reject [incoming|outgoing]


```

Then you know that the --dry-run option is optional. If you are using the "default" part of the command, then you have to specify either allow, deny or reject. You can optionally add either the words "incoming" or "outgoing".

---

### Post by DD70 on 2009-11-29
> **frank002 said:**
> The Ubuntu firewall is UFW (Uncomplicated Firewall). It should come enabled already. To check open a terminal and type " sudo ufw status" without quotation marks. You are then prompted for your password. Type your password and it should tell you the status of  UFW. If for any reason it is disabled, type "ufw enable", again, without quotations. That is all.
Followed the above and then got 

owner@owner-desktop:~$ sudoufw status
bash: sudoufw: command not found
owner@owner-desktop:~$ sudo ufw status
[sudo] password for owner: 
Status: inactive
owner@owner-desktop:~$ ufw enable
ERROR: You need to be root to run this script
owner@owner-desktop:~$ 


How do i get to be root to turn it on, Or do i infact need too?
Is inactive the same as diabled?

---

### Post by u.b.u.n.t.u on 2009-11-29
> **gumstool said:**
> Do I need a firewall , and if so what do other users recommend ?

I recommend Firestarter.
[http://www.fs-security.com/](http://www.fs-security.com/)

You can download it via Ubuntu.

---

### Post by bodhi.zazen on 2009-11-29
> **DD70 said:**
> Followed the above and then got 

owner@owner-desktop:~$ sudoufw status
bash: sudoufw: command not found
owner@owner-desktop:~$ sudo ufw status
[sudo] password for owner: 
Status: inactive
owner@owner-desktop:~$ ufw enable
ERROR: You need to be root to run this script
owner@owner-desktop:~$ 


How do i get to be root to turn it on, Or do i infact need too?
Is inactive the same as diabled?

inactive = disabled.

You need to use sudo (run as root).

```
sudo ufw enable
```

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Virtual Liberty on 2009-11-29
> **u.b.u.n.t.u said:**
> I recommend Firestarter.
[http://www.fs-security.com/](http://www.fs-security.com/)

You can download it via Ubuntu.

It's haven't been updated since 2005 :-\"

---

### Post by DD70 on 2009-11-29
> **bodhi.zazen said:**
> inactive = disabled.

You need to use sudo (run as root).

```
sudo ufw enable
```

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")
many thank all aok now

---

### Post by bodhi.zazen on 2009-11-30
> **DD70 said:**
> many thank all aok now

You are most welcome, glad it is working for you.

---

### Post by Paqman on 2009-11-30
> **u.b.u.n.t.u said:**
> I recommend Firestarter.
[http://www.fs-security.com/](http://www.fs-security.com/)

You can download it via Ubuntu.

I wouldn't recommend firestarter, it's waaaaaaay old. It doesn't seem to be actively maintained any more.

---

### Post by u.b.u.n.t.u on 2009-11-30
Don't like Firestarter, then how about Smoothwall?

Last update 8th January 2009.

[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by u.b.u.n.t.u on 2009-11-30
> **Virtual Liberty said:**
> It's haven't been updated since 2005 :-\"

> **Paqman said:**
> I wouldn't recommend firestarter, it's waaaaaaay old. It doesn't seem to be actively maintained any more.

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)
"Download documentation
Firestarter manual in PDF format Firestarter User's Manual (Updated November 26 2009 )"

The manual was updated 4 days ago. 

Firestarter hasn't been updated, likely because there is no need.

Until such time as it is made clear that Firestarter is somehow deficient, I stand by my recommendation of Firestarter. ;)

---

### Post by Paqman on 2009-11-30
> **u.b.u.n.t.u said:**
> 
Firestarter hasn't been updated, likely because there is no need.


Well, there's a fair few bugs open on [Bugzilla]("https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter").

---

### Post by u.b.u.n.t.u on 2009-11-30
> **Paqman said:**
> Well, there's a fair few bugs open on [Bugzilla]("https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter").

No doubt it isn't perfect. If there is something better I would change. I haven't found anything better and so I use it and hence I recommend it or otherwise I wouldn't use it.

;)

---

### Post by bodhi.zazen on 2009-11-30
> **u.b.u.n.t.u said:**
> No doubt it isn't perfect. If there is something better I would change. I haven't found anything better and so I use it and hence I recommend it or otherwise I wouldn't use it.

;)

Well, all those bug reports kind of argue against your previous statement:

> **u.b.u.n.t.u said:**
> Firestarter hasn't been updated, likely because there is no need.

As has been pointed out, Firestarter is no longer maintained, not because there are no bugs, but because there are no longer any upstream maintainers.

If you prefer Firstarter, go for it. But there is no need to mis-represent Firestarter or it's shortcomings either.

I would suggest there are alternate tools, some of which work better for others, and some of which are better maintained.

If you ever wish to look at a similar alternate to Firestarter, take a look at ufw. If you wish to use a GUI, use GUFW.

---

### Post by u.b.u.n.t.u on 2009-11-30
> **bodhi.zazen said:**
> Well, all those bug reports kind of argue against your previous statement:

There are bugs in Ubuntu too you know. Does that stop you from using it? Well no, apprarently not! Now where exactly is there a bug free GUI firewall for linux?


> **bodhi.zazen said:**
> 
If you prefer Firstarter, go for it. But there is no need to mis-represent Firestarter or it's shortcomings either.

The only misrepresentation is your level of English comprehension!

---

### Post by bodhi.zazen on 2009-11-30
> **u.b.u.n.t.u said:**
> There are bugs in Ubuntu too you know. Does that stop you from using it? Well no, apprarently not! Now where exactly is there a bug free GUI firewall for linux?

I did not claim that Ubuntu was free of bugs nor did I claim that ubuntu has not been updated since 2005 "because there is no need".

No need to get angry or lash out simply because your claim that Firestarter is in no need of updates has been refuted.

---

### Post by u.b.u.n.t.u on 2009-11-30
> **bodhi.zazen said:**
> your claim that Firestarter is in no need of updates has been refuted.

Feel free to quote me where I have stated that "Firestarter is in no need of updates". I would never state that of any software, ever. Period!

As for me I am going to make a cuppa coffee and will not respond further in this thread/post.

Good day to you!

;)

* I said:

"Firestarter hasn't been updated, likely because there is no need.

Until such time as it is made clear that Firestarter is somehow deficient, I stand by my recommendation of Firestarter."

They updated the manual a few days ago. If Firestarter was a liability I think that either they would have stated such, removed it or Ubuntu would NOT have added it as a download option. That Firestater can be downloaded by Ubuntu is all the assurance I need that it is safe to use. THAT is what is implied by what I wrote.

---

### Post by lisati on 2009-11-30
> **u.b.u.n.t.u said:**
> I recommend Firestarter.
[http://www.fs-security.com/](http://www.fs-security.com/)

You can download it via Ubuntu.

:confused:The last time I checked Firestarter wasn't a firewall but a GUI front end for iptables. :rolleyes:

---

### Post by manny43 on 2009-11-30
I installed FIRESTARTER did not know about ufw( this is my 5th day running UBUNTU).Should i remove
FIRESTARTER and enable ufw?

---

### Post by bodhi.zazen on 2009-11-30
> **manny43 said:**
> I installed FIRESTARTER did not know about ufw( this is my 5th day running UBUNTU).Should i remove
FIRESTARTER and enable ufw?

A better question is , what are you using a firewall for ? If you are new to Ubuntu , I strongly sugget you read the Security Sticky at the top of these forums as Linux security is different enough from Windows it is probably worth your time to do so.

If you are happy with Firestarter, there is no need to change.

If you wish to remove it, be sure to completely remove it by using the purge option :

```
sudo apt-get purge firestarter
```

I would tend to tell you, if it is not broken, don't fix it. With that said, you would almost certainly find ufw and Gufw adequate for your needs.

If you would like, there are a number of how-to's on ufw/gufw and I recently bloged on how to use them :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

