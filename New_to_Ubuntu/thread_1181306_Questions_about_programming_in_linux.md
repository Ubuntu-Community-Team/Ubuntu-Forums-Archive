---
title: "Questions about programming in linux"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by bzm3r on 2009-06-07
I have only recently made the linux switch, and before that, I was a Windows user. I have been programming for a year or so now (ever since I started school), and used to do most of my programming in Visual Studio.

I was quite fond of it (I loved placing "watches" on variables, going through the program step by step, etc. to make my debugging easier), and I am wondering how I can accomplish similar things with Ubuntu.

I have been exposed to the two major text editors that are very commonly used for programming by linux users: emacs and vim, but they don't have many of the features that Visual Studio seems to have (for debugging)...but perhaps I have not been 'exposed' enough.

Thus, I am wondering if seasoned programmers could give me some feedback based on their experience/on the way they do things, in order to help me choose a good application (or set of applications) to help me with my programming.

---

### Post by QIII on 2009-06-07
You won't really be programming for "Ubuntu", just for an OS that is not Windows.  Remember that there are literally hundreds of Linux distributions of all sorts of shapes and colors out there.  And some languages (like Java) are platform independent.

Emacs and Vim are not IDEs as you would be used to calling Visual Studio.  Both of them are very useful for for the beginner learning other languages and can continue to be used by advanced users for the full development cycle.

If you want an IDE as you are used to with Visual Studio, I can suggest NetBeans (which I use for Java development, but it can be used for many other languages) or kdevelop.

Just be aware that things will be different.  Don't be confused between "different" and "wrong".

You learned to speak English (I assume) natively as a child.  You might find learning German difficult.  However, German kids learned German just fine.  The same will apply for Windows/Visual Studio -> Linux/programming tool of choice.

I'm sure that a number of people will chime in momentarily with their preferred tools.  All of them may be useful to you, so don't feel committed to one in particular until you have had a chance to work with them and decide which suits YOUR needs.

---

### Post by Temposs on 2009-06-07
There are several IDEs that very much achieve the same kind of result as Visual Studio.

for Java or C++, you can use Eclipse. A lot of people like that.

---

### Post by pbpersson on 2009-06-07
I went from Visual Basic.NET into Java and I use Netbeans.

In Java I can have the full set of capabilities I grew to expect in Visual Studio.  I can develop my code just once and since it executes using the JRE, it will (in theory at least) work on any computer anywhere without any extra coding.

I have already copied many of my creations which I have written on Linux over to Windows and they work fine there.  I have not tested them on Mac because I don't own one.

---

### Post by jpkotta on 2009-06-08
Emacs has a debugger mode: gud (grand unified debugger).  I've used it with the Perl debugger and gdb.  You may also like to check out ddd or other frontends for gdb.  Really, it's not that hard to use gdb directly once you're used to it, and then you can script it.

---

### Post by CJ Master on 2009-06-08
I'm not an expert on the subject, but I belive Mono is designed for people migrating from the .NET microsoft programing suites.

What IDE you want really depends on what you're programing in. GEDIT is an awesome all-around programer writer. Wing IDE is excelent for Python. Etc...

---

### Post by directhex on 2009-06-08
MonoDevelop includes a step-through debugger. Although you'll need to use my PPA to get it working on Mono apps

---

### Post by ad_267 on 2009-06-08
MonoDevelop also supports C and C++, and is very similar to Visual Studio. I use vim myself, with gdb for debugging.

---

### Post by Mornedhel on 2009-06-08
> **bzm3r said:**
> I have been exposed to the two major text editors that are very commonly used for programming by linux users: emacs and vim, but they don't have many of the features that Visual Studio seems to have (for debugging)...but perhaps I have not been 'exposed' enough.

I would like to point that emacs has every feature Visual Studio has, and many more that are unrelated to coding. It just takes some customizing and a whole lot of getting used to the emacs keybindings, which is why it's quite hard to take up for newcomers (even experienced programmers). emacs IS an IDE once you install the right packages.

As another poster said, GDB is integrated in emacs via the GUD. You also have access to almost-intellisense-like completion and many other features.

---

### Post by directhex on 2009-06-08
> **Mornedhel said:**
> and many more that are unrelated to coding. 

Once you get used to a text editor with built-in therapist, how could you go back?

---

