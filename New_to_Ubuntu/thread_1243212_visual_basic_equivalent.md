---
title: "visual basic equivalent?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-08-18
Hi,
I am fast tracking on Ubuntu knowledge.
Is there an equivalent Programming package to Windows Visual Basic, that will run on Ubuntu?

kenmac2

Completed.

---

### Post by Tclarkie on 2009-08-18
add/remove wxFormBuilder

---

### Post by ganeshmallyap on 2009-08-18
You may try MonoDevelop a open source project from Novel. It can support visual basic.net programming.  There is another vb similar programming application by name Gambas.  But I have not used it though.

---

### Post by tarps87 on 2009-08-18
> **kenmac2 said:**
> Hi,
I am fast tracking on Ubuntu knowledge.
Is there an equivalent Programming package to Windows Visual Basic, that will run on Ubuntu?

kenmac2

What do you mean by equivalent programming package, do you want an IDE that works with vb on Ubuntu or do you mean a language that is equivalent to vb or both?
The mono project allows vb development on Linux but I don't understand why you would want to use a microsoft/ windows specific language on anything other than a windows os.
For an IDE which works with a native language I would recommend Netbeans, however if you still want to use the language vb I will leave that up to someone else as I avoid using it.

---

### Post by directhex on 2009-08-18
> **tarps87 said:**
> What do you mean by equivalent programming package, do you want an IDE that works with vb on Ubuntu or do you mean a language that is equivalent to vb or both?
The mono project allows vb development on Linux but I don't understand why you would want to use a microsoft/ windows specific language on anything other than a windows os.
For an IDE which works with a native language I would recommend Netbeans, however if you still want to use the language vb I will leave that up to someone else as I avoid using it.

It's unquestionably a terrible, terrible language which I'd never ever recommend anyone use.

However, I packaged it specifically for people like this guy, to allow them to make that choice themselves. install [monodevelop](apt:monodevelop) for an IDE, and [mono-vbnc](apt:mono-vbnc) for the VB.NET compiler

---

### Post by trilobite on 2009-08-18
> **ganeshmallyap said:**
> You may try MonoDevelop a open source project from Novel. It can support visual basic.net programming.  There is another vb similar programming application by name Gambas.  But I have not used it though. 
I agree - I think Gambas might be your best bet, kenmac2. Here's the URL - 
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

The website does say that Gambas is not a "clone" of VB, but apparently that's because (according to the developer) VB has lots of inconsistencies, bugs and so on. ( I couldn't comment as I've used neither Gambas nor VB ). 

Anyway, from what I can tell, Gambas does seem to be pretty good (for a VB-ish language ;) ). 
- trilobite

---

### Post by kenmac2 on 2009-08-18
As I'm operating a dual boot (XP/Ubuntu) I can still use VB within the XP OS.
I'm just looking into the future where I may decide to give XP the flick.
I just need to be able to create simple Form-based control programs within Ubuntu, that can process data/input and control comms. (similar to VB within XP)
Thanks for the pointers that you have provided.

kenmac2

---

### Post by theozzlives on 2009-08-18
There's always Lazarus. It's Pascal, so it's more like Delphi. Much stronger language. It's in the repos.

---

### Post by spribo on 2009-08-18
I have already used both VB.NET and Gambas, I can tell that Gambas is far better than VB.NET. As an example, in order to use databases with VB, you have to use LINQ and create entity classes and set the "Copy to output" property "Do not copy" and so on, whereas in Gambas you have just to establish a connection. Gambas is simple and fast and lightweight, whereas VB slow and bloated.

---

### Post by kalaharix on 2009-08-18
Gambas is great for me (networked database work, none of that fancy web thundercloud stuff). Very robust. I must say, as a very-average ex-VB6 programmer, that I found the documentation hard going and think I will forever be in learning mode with Gambas. Don't think you will plug in your VB code and press the compile button. I am currently running 2 POS terminals and a separate goods receiving machine with Gambas2 and MySQL on what is basically the conversion of VB6 programs.

Just remember it works on Linux only which some might have a problem with. I would also probably not use it to develop the next killer-app for wide scale distribution. I suspect this is more a criticism of Linux, dependencies and multiple distros than a criticism of Gambas itself. Roll on the day when Ubuntu and Linux are synonymous :)

rgds

---

### Post by kenmac2 on 2009-08-18
Thanks guys,
I'll look at Gambas - it seems the most suitable.

kenmac2

---

### Post by richaustin on 2009-08-18
I'd say MonoDevelop if you really want to continue along the Microsoft route since it is a version of VB.Net in a sense. Microsoft have helped support it which ought to tell you something - positive or negative is your decision.
I'm a VB Developer but only use Windows at work. I'd personally look at Eclipse Java, or Anjuta. Only you can decide what is right for you - try various things and see what you think. Mono is easy if you can write in VB.Net but, as I said, I choose not to use it at home.

Rich

---

### Post by ganeshmallyap on 2009-08-20
> **theozzlives said:**
> There's always Lazarus. It's Pascal, so it's more like Delphi. Much stronger language. It's in the repos.

I tried to install Lazarus in my Ubuntu Jaunty yesterday.  It is working fine.  I felt the very appearance of the IDE seems to be very foreign.  For example, the windows and menus were popping up in a unusual manner (not similar to gnome style).  

But it seems interesting, will try to learn it in coming days.

---

### Post by theozzlives on 2009-08-20
> **ganeshmallyap said:**
> I tried to install Lazarus in my Ubuntu Jaunty yesterday.  It is working fine.  I felt the very appearance of the IDE seems to be very foreign.  For example, the windows and menus were popping up in a unusual manner (not similar to gnome style).  

But it seems interesting, will try to learn it in coming days.

[http://wiki.lazarus.freepascal.org/Lazarus_Tutorial]("http://wiki.lazarus.freepascal.org/Lazarus_Tutorial")

I'm just a Pascal fan (since Turbo Pascal 7.0 for DOS), it's simple but powerful. When Delphi came out, I was excited, cause I was tired of all the dependencies (or "Runtime Libraries") VB needed to run. Plus it was Pascal.

---

### Post by ganeshmallyap on 2009-08-20
Thank you so much for the link [URL="http://ubuntuforums.org/member.php?u=420456"]theozzlives.  
[/URL]

---

### Post by directhex on 2009-08-20
> **theozzlives said:**
> [http://wiki.lazarus.freepascal.org/Lazarus_Tutorial]("http://wiki.lazarus.freepascal.org/Lazarus_Tutorial")

I'm just a Pascal fan (since Turbo Pascal 7.0 for DOS), it's simple but powerful. When Delphi came out, I was excited, cause I was tired of all the dependencies (or "Runtime Libraries") VB needed to run. Plus it was Pascal.

To bring things full circle, the guy behind C# is the same guy behind Turbo Pascal and Delphi

---

### Post by garryknight on 2009-08-20
It seems that no one mentioned [KBasic]("http://www.kbasic.com/").

---

### Post by moster on 2009-09-01
Cannot believe how small community Gambas and Kbasic have. If Gambas was on windows it would have million users. I will use Gambas for my little future apps :)

Tell us how it is going.

---

### Post by scorp123 on 2009-09-01
> **kenmac2 said:**
>  I just need to be able to create simple Form-based control programs within Ubuntu, that can process data/input and control comms. Why not use shell scripting and zenity then? It's simple and stupid and it just works. :D

[http://library.gnome.org/users/zenity/stable/](http://library.gnome.org/users/zenity/stable/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

[http://www.freesoftwaremagazine.com/columns/saving_my_sanity_zenity_shell_script_interaction_gui](http://www.freesoftwaremagazine.com/columns/saving_my_sanity_zenity_shell_script_interaction_gui)

---

