---
title: "Trustworthy Add-Ons/Open Ports"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by TortureQueen on 2010-07-28
I'm sorry if these are stupid questions, but I have some questions about some FireFox add-ons.  Does NoScript open any ports?  Does Ad-Blocker Plus open any ports?  Thanks, guys.

---

### Post by lovinglinux on 2010-07-29
There is a lot of confusion about what "open port" means. An open port is not just that your machine can be reachable through a certain port, but also that someone would be able to connect remotely to some application in your machine. To do that the port must be unblocked in the firewall and you must be running an application capable of listening to incoming unrequested connections. 

Your browser can do that? No. You browser only accepts data from connections that have already created by it. Even if you don't have a firewall or a router, is not possible for someone on the Internet to type your IP on some cracker software and magically connect to your Firefox and take control over it. Why? Because Firefox is not a server and thus do not listen to incoming unrequested connections on any port. 

Additionally, Ubuntu doesn't come by default with relevant open ports. Which means that any connection attempts coming from outside, that were not originated by your machine will be rejected. This means all ports are closed by default, even if you don't have a firewall or a router.

What types of programs are capable of opening ports? Servers. For example a web server like Apache or even a BitTorrent client like Transmission are servers, because they allow remote users to request connections in order to perform different tasks. This means they indeed open ports.

Can extensions open ports? Yes. Do they? Not usually. The only extensions I know that can do that are [FireTorrent]("https://addons.mozilla.org/en-US/firefox/addon/10931/") and [Plain Old Server]("https://addons.mozilla.org/en-US/firefox/addon/3002/"), because they add server functionality to your browser, usually using third party libraries. You might find others if you search the extension database for "[server]("https://addons.mozilla.org/en-US/firefox/search/?q=server&cat=all")".

Most of the extensions available for Firefox will not open any ports, although they might send information to a remote server about pages you visit for example, since some extensions need that type of information to provide their functionality properly. Usually this type of extensions are those that have a privacy police when you download them.

Are extension safe? Approved extensions are. Why? Because Mozilla inspect the code of ALL approved extensions manually, including updates. They don't approve extensions with any kind of problem, even if they are not security related.

Keep in mind there are 4 types of extensions in Mozilla web site: public, featured, self-hosted and experimental. These extension types can be identified by their download icons and colors.

Public and Feature are safe because they are reviewed by Mozilla.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164865&stc=1&d=1280381061[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164867&stc=1&d=1280381061[/IMG]

Experimental and Self-Hosted are not entirely safe, because they are not reviewed by Mozilla.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164866&stc=1&d=1280381061[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164868&stc=1&d=1280381061[/IMG]

Being self-hosted does not mean they are dangerous. Some developers prefer to host their extensions on their own web sites, to avoid the review process in order to make their extensions available to users as soon as possible. Nevertheless, since these extensions are not reviewed, there is no guarantee that the extension would not contain malicious code or errors that could interfere with the browser functioning.

"Experimental" are those extensions that hasn't been reviewed yet or hasn't been approved for some reason. The are marked as not reviewed when the developer just submitted it for review or because the developer is still developing it and just want feedback from beta testers or because the extension has issues and thus hasn't been approved yet.

So using extensions that are not reviewed or self-hosted requires caution. That being said, I use experimental extensions myself and never had issues, although there were a couple of [malicious extensions found recently](http://ubuntuforums.org/showthread.php?t=1530536). They are very rare tho. IMO, the main problem with  experimental extensions, aside from security and privacy issues, are that they might contain bad written code, which could break other extensions and Firefox or even cause data loss in your system. So if you are about to install an experimental extension, look the extension version history to see if it has been approved before or not, look the user reviews and look the author profile to see if he is an experienced developer and how many approved extension exists on his portfolio.

About NoScript and AdBlock Plus, they are perfectly safe to use and must have if you are worried about browser security. They do not open ports btw.

NoScript has been downloaded 70,613,063 while AdBlockPlus has been downloaded 87,736,386 times and has [10,260,700 daily users]("https://addons.mozilla.org/en-US/statistics/addon/1865").

In case you haven't figure out yet, [I'm a Firefox extension developer]("https://addons.mozilla.org/en-US/firefox/user/4352153") :)

---

### Post by TortureQueen on 2010-07-31
Thank you so much LovingLinux.  I'm going to download both NoScript and ABP.

---

### Post by Rubi1200 on 2010-07-31
If you are concerned about browser privacy, you might also want to take a look at BetterPrivacy (also available on the Mozilla addons site).
 
This article explains what BetterPrivacy deals with:
 
[http://en.wikipedia.org/wiki/Local_Shared_Object](http://en.wikipedia.org/wiki/Local_Shared_Object)
 
For the default security policies on Ubuntu (especially the no open ports policy):
 
[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

---

