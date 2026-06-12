---
title: "what is mono??"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Jordanbadangayon on 2011-05-07
What is mono??? I'm sorry if it's a dumb question but I don't really know why a lot of people hate Banshee for using mono. I love Banshee and I think it's the best player out there. But can anyone tell me what mono is?? and Why Linux people hate it? The informations I got from googling it seem not to be such a bad thing.  :)

---

### Post by Paqman on 2011-05-07
It's an open source implementation of Microsoft's .NET environment. People hate on it purely on the strength of the whiff of Microsoft, but a lot of developers seem to quite like .NET, so I think it's great that we have our own version of it. It's a bit like the way we have open source versions of things like Java.

Bottom line: Mono is open source, and 99.9% of all the terrible things people accuse it of are just complete rubbish.

---

### Post by Quadunit404 on 2011-05-07
> **Paqman said:**
> Bottom line: Mono is open source, and 99.9% of all the terrible things people accuse it of are just complete rubbish.

+&#8734;

But yeah, Mono = .NET but open-source and due to its use of Microsoft code there has been a lot of propaganda and scaremongering against it (particularly from the FSF.) If you see pages like "OH NOES MONO USES MICRO$HIT CODE USE IT AND YOU'RE DOOMED TO BEING SUED TO HELL AND BACK!!!" ignore it.

---

### Post by gandaran on 2011-05-07
my only reason I dislike mono is all those microsoft dll's and exe's, look in /usr/lib/banshee to see what I mean, we don't need them in Linux!

---

### Post by pbpersson on 2011-05-07
> **gandaran said:**
> my only reason I dislike mono is all those microsoft dll's and exe's, look in /usr/lib/banshee to see what I mean, we don't need them in Linux!

Fascinating, it is like having Microsoft right here on our doorstep.  Was any of that code written by Microsoft?

So....how does it execute the exe files, I thought those could only be used if I had Wine installed?

---

### Post by robgraves on 2011-05-07
> **gandaran said:**
> my only reason I dislike mono is all those microsoft dll's and exe's, look in /usr/lib/banshee to see what I mean, we don't need them in Linux!

wow, that's kinda interesting

---

### Post by 3rdalbum on 2011-05-07
Mono doesn't use Microsoft code.

Microsoft has promised not to sue over Mono (in fact, they've helped develop software that runs on Mono - see Moonlight) so the whole thing is a non-issue. Some people have been trying to pick loopholes in Microsoft's statement, but really the threat has ended.

Mono isn't very often used, anyway. If Microsoft wanted to sue some well-used Linux software that infringes patents and helps decrease the number of Windows licenses purchased, they'd go after Wine.

---

### Post by madjr on 2011-05-07
well, i think that mono is good, (probably better than .Net itself in many ways).

sure there will always be some fears of msft filing some lawsuit someday, but until that day comes (if ever), we should keep using the programs built with it normally.

if some people/developers come from windows and find mono easy to code, then there is no real reason (yet) to stop using it.

on the other hand that fear is not a bad thing, because we are prepared almost completely (like 80%) to drop mono if that ever happens, we have some very good alternatives just in case.

---

### Post by 3rdalbum on 2011-05-07
> **gandaran said:**
> my only reason I dislike mono is all those microsoft dll's and exe's, look in /usr/lib/banshee to see what I mean, we don't need them in Linux!

They are called ".dll" and ".exe" because that's what non-native .NET programs expect them to be called. They do not contain Microsoft code, and they are Mono bytecode libraries and programs, NOT Windows library and Windows executable formats.

---

### Post by demilord on 2011-05-07
Mono is .NET for linux, like Moonlight is Silverlight rip off...

It's a nono for me but then again gnome depends on mono these days...

---

### Post by demilord on 2011-05-07
> **3rdalbum said:**
> They are called ".dll" and ".exe" because that's what non-native .NET programs expect them to be called. They do not contain Microsoft code, and they are Mono bytecode libraries and programs, NOT Windows library and Windows executable formats.

Then why did they name it that way, is mono programmed by microsoft monkeys?

---

### Post by 3rdalbum on 2011-05-07
> **demilord said:**
> It's a nono for me but then again gnome depends on mono these days...

No, Gnome's core doesn't depend on Mono and that's the way the Gnome devs keep it. Gnome does have a .NET-like substitute called Vala, that parts of Gnome use.

---

### Post by 3rdalbum on 2011-05-07
> **demilord said:**
> Then why did they name it that way, is mono programmed by microsoft monkeys?

> **They are called ".dll" and ".exe" because that's what non-native .NET programs expect them to be called.**

Otherwise, non-native .NET programs won't work on anything except Windows.

> **They do not contain Microsoft code**

---

### Post by Jordanbadangayon on 2011-05-07
Thanks for all the replies... Well, I guess those people who hate mono are not really well-informed...  :)

---

### Post by 3rdalbum on 2011-05-07
> **Jordanbadangayon said:**
> Thanks for all the replies... Well, I guess those people who hate mono are not really well-informed...  :)

Some of them are sprouting rabbid anti-Microsoft rubbish, but I think most of them just care a lot about the Linux desktop and are scared that Microsoft will find a way to take it away from them. I find it difficult to criticize people who have your best interests at heart.

---

### Post by Frogs Hair on 2011-05-07
Information

[http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by pbpersson on 2011-05-07
Since there are some components of Mono for which Microsoft holds the patents, would it be within their legal rights to wait several years until Mono code is in a large amount of Linux applications and then demand a licensing fee for each copy of Linux which uses the technologies they created?

---

### Post by directhex on 2011-05-07
> **pbpersson said:**
> Since there are some components of Mono for which Microsoft holds the patents, would it be within their legal rights to wait several years until Mono code is in a large amount of Linux applications and then demand a licensing fee for each copy of Linux which uses the technologies they created?

That depends. It's been **TEN YEARS** since Mono was started, and still nobody's named these patented components.

In fact, nowadays Mono bundles a few libraries which Microsoft released under FOSS licenses - including full rights to any patents that code may implement (ASP.NET MVC, DLR, F#, etc)

---

### Post by rx007 on 2011-05-07
> **gandaran said:**
> my only reason I dislike mono is all those microsoft dll's and exe's, look in /usr/lib/banshee to see what I mean, we don't need them in Linux!

yeah, not only banshee. tomboy notes and gbrainy as well. :shock:

---

### Post by Paqman on 2011-05-07
> **demilord said:**
> Then why did they name it that way, is mono programmed by microsoft monkeys?

Because the idea is to be *compatible* with .NET, which uses those file extensions.

---

### Post by pbpersson on 2011-05-07
> **directhex said:**
> That depends. It's been **TEN YEARS** since Mono was started, and still nobody's named these patented components.

In fact, nowadays Mono bundles a few libraries which Microsoft released under FOSS licenses - including full rights to any patents that code may implement (ASP.NET MVC, DLR, F#, etc)

I [found a web site]("http://www.groklaw.net/articlebasic.php?story=20080312151954507") where some law experts in the FOSS community examined the wording of the Microsoft agreement and had quite a few concerns about the loopholes.

In my scenario, Microsoft would only use this as a legal weapon at a future date when:

1.  A significant portion of each Linux distribution used Mono
2.  Linux was threatening the market dominance of Windows

Neither of these conditions exist today.

---

### Post by Old_Grey_Wolf on 2011-05-07
<humor>

Mononucleosis, or mono, is a viral infection causing fever, sore throat, and swollen lymph glands. Mono may begin slowly with fatigue, a general ill feeling, headache, and sore throat. The sore throat slowly gets worse. Your tonsils become swollen and develop a whitish-yellow covering. The lymph nodes in the neck are frequently swollen and painful. A pink, measles-like rash can occur.

</humor>

:lolflag:

---

### Post by Georgia boy on 2011-05-07
> **Old_Gray_Wolf said:**
> <humor>

Mononucleosis, or mono, is a viral infection causing fever, sore throat, and swollen lymph glands. Mono may begin slowly with fatigue, a general ill feeling, headache, and sore throat. The sore throat slowly gets worse. Your tonsils become swollen and develop a whitish-yellow covering. The lymph nodes in the neck are frequently swollen and painful. A pink, measles-like rash can occur.

</humor>

:lolflag:
=D>:twisted:

---

### Post by directhex on 2011-05-07
> **pbpersson said:**
> I [found a web site]("http://www.groklaw.net/articlebasic.php?story=20080312151954507") where some law experts in the FOSS community examined the wording of the Microsoft agreement and had quite a few concerns about the loopholes.

In my scenario, Microsoft would only use this as a legal weapon at a future date when:

1.  A significant portion of each Linux distribution used Mono
2.  Linux was threatening the market dominance of Windows

Neither of these conditions exist today.

You're conflating multiple issues, and not replying to what I said.

---

### Post by pbpersson on 2011-05-08
> **directhex said:**
> You're conflating multiple issues, and not replying to what I said.

Well, you said that you did not know what components in .NET Microsoft had released under the FOSS license.

The web page I supplied linked to a Microsoft web page where I found the following .NET assemblies covered under that license:

> [MC-NBFS]: .NET Binary Format: SOAP Data Structure RFC 2125 – Bandwidth Allocation Protocol (BAP)

[MC-NBFSE]: .NET Binary Format: SOAP Extension RFC 2131, RFC 2132, and RFC 3361- Dynamic Host Configuration Protocol (DHCP)

[MC-NBFX]: .NET Binary Format: XML Data Structure RFC 2205, RFC 2209, and RFC 2210– Resource Reservation Setup (RSVP)

[MC-NMF]: .NET Message Framing Protocol Specification RFC 2222 – Simple Authentication and Security Layer (SASL)

[MC-NPR]: .NET Packet Routing Protocol Specification 

Additionally, the article I was reading said that within Mono there was something called the "Microsoft Compatibility Pack" which was "a gift" from Microsoft to the FOSS community.  

I am sorry, I do not have time to research all this.  I thought someone would know something about this.

In the past I have been involved in projects depending upon the future plans of Microsoft only to have them change their direction and leave us hanging.  Millions of people were affected but that makes no difference to them.  Any project now which depends upon Microsoft I avoid because I have been burned in the past.

This is exactly why I am using Java technology for all my cross-platform development projects.

How much of Mono is based on MS technology that they can pull the plug on?

---

### Post by directhex on 2011-05-08
> **pbpersson said:**
> Well, you said that you did not know what components in .NET Microsoft had released under the FOSS license.

Having personally done an audit of Mono's licensing (all 40,000 files), I have a reasonable idea of what they've released under FOSS licenses.

I said there was no documented case of a Microsoft patent infringed in Mono.

> The web page I supplied linked to a Microsoft web page where I found the following .NET assemblies covered under that license:

It's not a source license. The Community Promise is a patent grant for unnamed patents (i.e. "if you end up infringing a patent we own in order to implement $FOO, don't worry about it"), almost identical in language to that which covers ODF from Oracle. The things you list are specifications covered by the Open Specification Promise (which is a patent grant similar to the Community Promise, but with different rules regarding subsets of the spec).

> Additionally, the article I was reading said that within Mono there was something called the "Microsoft Compatibility Pack" which was "a gift" from Microsoft to the FOSS community.

No, there's no such thing.

> In the past I have been involved in projects depending upon the future plans of Microsoft only to have them change their direction and leave us hanging.  Millions of people were affected but that makes no difference to them.  Any project now which depends upon Microsoft I avoid because I have been burned in the past.

Mono is what we call "Free & Open Source technology". What this means, amongst other things, is that you can't be "left hanging" by a change in the framework, because you have the source code right there - if need be, you can use the source for the last version which did what you need, and do whatever with it. As an example, Mono 2.8+ no longer support execution of .NET 1.1 apps, but you're welcome to use 2.6.7 for 1.1 support - or use Mono's remapping support to execute 1.1 apps as 2.0 or 4.0

> How much of Mono is based on MS technology that they can pull the plug on?

I'm not sure I fully understand your hypothetical scenario. What "plug" will they be pulling, exactly? Mono implements published ECMA/ISO specifications, plus additional libraries, plus some of its own special sauce. You need to be more clear about your doomsday scenario - preferably in a way grounded in reality - to explain exactly how "Mono is based on MS technology".

---

### Post by pbpersson on 2011-05-08
I just read articles on several web sites regarding this and they all contain the following text.  You have never heard of this?

> Microsoft compatibility stack: The Microsoft compatibility stack provides a pathway for porting Windows .NET applications to Linux. They comprise ADO.NET, ASP Dot Net Development, and Windows.Forms, among others. They are not covered by ECMA standards, some of them stay subject to patent fears and concerns.

---

### Post by directhex on 2011-05-08
> **pbpersson said:**
> I just read articles on several web sites regarding this and they all contain the following text.  You have never heard of this?

It's not terminology I've ever seen used.

Okay, that's referring to various libraries which are implemented in Mono, duplicating functionality in Microsoft.NET, but which is not otherwise covered by applicable patent grants (of which there are three major categories).

Remember how a patent grant works, by the way - "When we wrote X, we believe our implementation covers a number of patents - we assume other implementations would also need those patents so grant you permission to use them". The existence of a patent grant for something in no way means all implementations of a specification require those patents.

The subset of technologies being discussed (e.g. ADO.NET, which is the standard library for talking to databases in .NET and is of course absolutely novel and impossible to find prior art for in, say, JDBC) relate to things which have no explicit or implicit patent grant. That doesn't mean a) that patents are infringed by all implementations e.g. Mono or Portable.NET, or b) that patents held on that technology are even valid or defensible in court, or c) that any patents are even held in the first place, or d) that any identified patent infringement can't be easily worked around.

---

### Post by Jordanbadangayon on 2011-05-15
Thanks for all the replies. It has been an interesting and informative discussion. :D

---

### Post by Wamiduku on 2011-05-20
Kind of odd that no one in this discussion mentioned that all Mono developers have been fired, [http://blog.wezeku.com/2011/05/17/now-its-confirmed-attachmate-really-did-axe-mono/](http://blog.wezeku.com/2011/05/17/now-its-confirmed-attachmate-really-did-axe-mono/)

I think there's a separate thread about it somewhere.

---

### Post by geoaraujo on 2011-06-13
I think there's **much more** about mono that what have been said. In a discussion about using Pinta (which uses mono) as an alternative to GIMP, an user named "Roy" expressed his concerns about the use of mono.

[ http://maketecheasier.com/pinta-image-editing-alternative-to-the-gimp#comment-81113821]("http://maketecheasier.com/pinta-image-editing-alternative-to-the-gimp#comment-81113821")

I believe it's worthy reading.

---

### Post by Elfy on 2011-06-13
There are plenty of mono threads in recurring discussion, no need to add to this one.

Closed

---

