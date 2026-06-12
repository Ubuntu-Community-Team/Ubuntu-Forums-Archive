---
title: "Mac software"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by snip3r8 on 2010-09-03
Can a person run mac software on linux? im mainly interested in getting itunes running and i dont want to use wine.

---

### Post by clive littlewood on 2010-09-03
Hi

I believe that mac os will run in the latest "virtualbox"

Check them out at virtualbox.com

Clive

---

### Post by snip3r8 on 2010-09-03
I know of virtualbox but i thought that with linux being unix based it wouldn't require much to get a mac app to run

---

### Post by scorp123 on 2010-09-03
> **clive littlewood said:**
>  I believe that mac os will run in the latest "virtualbox"  Be warned though this is is only legal if you have Apple Mac hardware. Apple regards running Mac OS X on non-Apple hardware as illegal and giving hints like that will draw attention from Apple's legal department. And for this reason the admins here might take pro-active action against you and e.g. lock this thread or even ban you for violating forum rules (e.g. the fact that illegal activities are not endorsed and not supported here).

---

### Post by scorp123 on 2010-09-03
> **snip3r8 said:**
> I know of virtualbox but i thought that with linux being unix based  Linux isn't "unix based". Technically it's a Unix emulator: It looks and feels like Unix ... but it's not based on it, it's a clean-room reimplentation of the same ideas.

Operating systems such as the various variations of BSD (FreeBSD, OpenBSD, NetBSD, PC-BSD ...) however indeed have historic roots in the original AT&T Unix source code. They are indeed "Unix based", both historically and technically.

> **snip3r8 said:**
>  it wouldn't require much to get a mac app to run And here's where you are mistaken. Underneath Mac OS X's shiny GUI there is a truckload of differences and Apple-proprietary additions. So it would actually require *a lot* IMHO. And Apple isn't really cooperative when it comes to such questions. Which is obvious: because then nobody would (need to) buy their hardware anymore .. and that's where Apple is making the money $$$

---

### Post by snip3r8 on 2010-09-03
> **scorp123 said:**
> Linux isn't "unix based". Technically it's a Unix emulator: It looks and feels like Unix ... but it's not based on it, it's a clean-room reimplentation of the same ideas.

Operating systems such as the various variations of BSD (FreeBSD, OpenBSD, NetBSD, PC-BSD ...) however indeed have historic roots in the original AT&T Unix source code. They are indeed "Unix based", both historically and technically.

 And here's where you are mistaken. Underneath Mac OS X's shiny GUI there is a truckload of differences and Apple-proprietary additions. So it would actually require *a lot* IMHO. And Apple isn't really cooperative when it comes to such questions. Which is obvious: because then nobody would (need to) buy their hardware anymore .. and that's where Apple is making the money $$$

i didnt think it would be illegal seeing as they give out itunes for free ,and on windows too

---

### Post by limestone on 2010-09-03
Linux aren't UNIX based, it's inspired of UNIX and it's UNIX-like.
Todays Mac Os x are Unix/Linux based deep down in the core but they still uses it's own API and languages..
If the application you would like to run in Linux is open-source you could port the app..

---

### Post by snip3r8 on 2010-09-03
anybody know of a petition to apple to make itunes on linux?

---

### Post by srs5694 on 2010-09-03
> **scorp123 said:**
> Be warned though this is is only legal if you have Apple Mac hardware. Apple regards running Mac OS X on non-Apple hardware as illegal and giving hints like that will draw attention from Apple's legal department. And for this reason the admins here might take pro-active action against you and e.g. lock this thread or even ban you for violating forum rules (e.g. the fact that illegal activities are not endorsed and not supported here).

Apple seems to be pretty tolerant on this score, so long as it's kept to a hobbyist level. There are several forums devoted to such activities, and AFAIK Apple's never tried to shut them down. Apple *has,* however, gone after PsyStar, which sold unauthorized Mac clones that used the same technologies that hobbyist Hackintosh users employ. The moderators here are pretty strict about such discussions, presumably erring on the side of caution rather than taking even a slight risk of legal action against their site.

As to the broader question, there are two big issues, neither of which has all that much to do with the Linux-vs-Unix issue that many of the posts so far have raised:


[list]
[*]Many OS X programs, probably including the iTunes application(s), are binary-only, so you can't recompile them on Linux or any other OS. Any similarity between two OSes at the source code level is meaningless without access to the source code or a binary compatibility layer in the target OS. This contrasts with, say, Emacs or OpenOffice.org, which can be recompiled from source for Linux, FreeBSD, Solaris, or other Unix-like OSes.
[*]Mac OS X includes a large number of OS support features that aren't implemented on other Unix or Linux systems. The entire OS X GUI is Apple-only, for instance -- most OS X applications don't use the X Window System GUI (the name "OS X" is entirely unrelated to "X Window System"). This means that a binary compatibility layer, similar to Wine, would be non-trivial to write (similar to Wine, which took a decade or so to become useful for any but trivial tasks and programs).
[/list]


You can, of course, petition Apple to port iTunes to Linux. If Linux becomes important enough in the desktop marketplace, they might even do so. I doubt if Linux is at that point right now, though.

In the short term, your best bet is probably to run the Windows version under Wine or some other Windows emulator. I see from its [Wine AppDb entry](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347) that iTunes runs with ratings that range from "garbage" to "silver," depending on the versions, so if you pick the right versions, you can probably get acceptable results. I can't help you with specifics, though, since I don't use iTunes. I realize you said you don't want to use Wine, snip3r8, but this really is the best option at the moment, AFAIK.

---

### Post by MCVenom on 2010-09-03
I know it's not quite the same, but I wanted to Mozilla Songbird is the closet thing to an iTunes competitor I've seen on any platform. They've discontinued Linux support, but [Nightingale]("http://getnightingale.com/") aims to pick up where Songbird left off.

I know this may not be helpful if you want iTunes for the purpose of buying apps, or the iTunes Music Store, or syncing apps and whatnot, but I thought I'd mention it in case someone finds it interesting.

---

### Post by scorp123 on 2010-09-04
> **srs5694 said:**
> Apple seems to be pretty tolerant on this score I think you are badly mistaken there. I know several "OS X86" sites which were forcefully closed down. Especially with US-based sites this was easy to achieve thanks to DMCA.

> **srs5694 said:**
>  There are several forums devoted to such activities, and AFAIK Apple's never tried to shut them down. Try a search engine maybe? :D

> **srs5694 said:**
>  The moderators here are pretty strict about such discussions, presumably erring on the side of caution rather than taking even a slight risk of legal action against their site.  And rightly so. Most of us here --even the moderators-- are volunteers. So who exactly is supposed to pay any legal fees if some lawyer decides to go after me? Mark Shuttleworth?? Yeah, very 'likely' to happen ... So there is only one way to keep this forum out of trouble: keep it clean and not tolerate such discussions more than necessary. That's why they have forum rules here.

> **srs5694 said:**
>  Many OS X programs, probably including the iTunes application(s), are binary-only, so you can't recompile them on Linux or any other OS. Any similarity between two OSes at the source code level is meaningless without access to the source code or a binary compatibility layer in the target OS.  Exactly.

> **srs5694 said:**
>  In the short term, your best bet is probably to run the Windows version under Wine or some other Windows emulator.  It works tip top under the 'PUEL' version of Oracle Virtualbox. (... the OSE release in the repos doesn't have USB-forwarding, just in case anyone wonders ...)

---

### Post by snip3r8 on 2010-09-05
> **scorp123 said:**
> Be warned though this is is only legal if you have Apple Mac hardware. Apple regards running Mac OS X on non-Apple hardware as illegal and giving hints like that will draw attention from Apple's legal department. And for this reason the admins here might take pro-active action against you and e.g. lock this thread or even ban you for violating forum rules (e.g. the fact that illegal activities are not endorsed and not supported here).

what if you run OSX on a virtual box in linux on a mac?

---

### Post by srs5694 on 2010-09-05
> **scorp123 said:**
> [quote=srs5694]Apple seems to be pretty tolerant on this scoreI think you are badly mistaken there. I know several "OS X86" sites which were forcefully closed down. Especially with US-based sites this was easy to achieve thanks to DMCA.[/quote]

There's at least one OSx86 site that shuts down every April 1 with such a notice as an April Fool's joke. I know of another site that Apple threatened in 2006, and they reorganized, but they didn't actually shut down. PsyStar has largely shut down, but they were a hardware manufacturer, and that's where Apple seems to draw the line.

> Try a search engine maybe? :D

I did. There were lots of hits on a story from 2006, but the domain is still active today, albeit not the exact URL cited back then. A Web search will also turn up several current active Hackintosh sites. There's even a book on the topic, published by Wiley.

> [quote=srs5694]The moderators here are pretty strict about such discussions, presumably erring on the side of caution rather than taking even a slight risk of legal action against their site.And rightly so. Most of us here --even the moderators-- are volunteers. So who exactly is supposed to pay any legal fees if some lawyer decides to go after me? Mark Shuttleworth?? Yeah, very 'likely' to happen ... So there is only one way to keep this forum out of trouble: keep it clean and not tolerate such discussions more than necessary. That's why they have forum rules here.[/quote]

I'm not trying to criticize the forum because of its censorship of such discussions. As you say, forum moderators probably couldn't withstand a legal attack from Apple. (A publisher like Wiley might be able to do so, OTOH.) I do, however, think that the *way* the moderators shut down such discussions could easily lead readers to incorrectly think that Apple has unleashed a band of rabid lawyers who pounce on any Internet discussion of Hackintosh activities, the way the RIAA attacks those who distribute MP3s on the Internet.

---

### Post by srs5694 on 2010-09-06
> **scorp123 said:**
> I think you are badly mistaken there. I know several "OS X86" sites which were forcefully closed down. Especially with US-based sites this was easy to achieve thanks to DMCA.

I don't mean to beat this issue to death or rouse the moderators' wrath, but I've done some more research on this, and there's an important point here about DMCA takedown notices generally, not just about Hackintosh issues:

In early 2006, Apple filed DMCA takedown notices against two sites. I found no information on one site except for that fact, and the domain is no longer active. The other site, though, is still active, as stated in my previous post. A Google search turned up lots of hits about the sites being taken down, but information on the resolution was buried rather late in the search results. It turns out that Apple was objecting to a *single link* to a particular piece of software. In such a case, the DMCA requires the site owner or ISP to remove the offending data; however, many ISPs are quite skittish about this, and so they shut down an entire site until the site's owner certifies that the offending material has been removed. This appears to be what happened to the site in question.

I bring this up because the general issues are much more broadly relevant than just the Hackintosh issue. If I were to post a download link to, say, the commercial version of WordPerfect 8 for Linux, that would put this site at risk for a DMCA takedown notice. Correcting the problem would be easy, but if the site's hosting provider was skittish, it might be down for a while.

---

