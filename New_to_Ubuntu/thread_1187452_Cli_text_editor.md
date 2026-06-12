---
title: "Cli text editor"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by A_M_S on 2009-06-14
Hello.

Since i'm not a big fan of vi, i would like to use another cli text editor.

Anyone have any suggestions?

Tnx.

---

### Post by unutbu on 2009-06-14
Wait for it...




Wait for it...





EMACS! hehe

(Install the emacs-snapshot package if you'd like to use ttf fonts.)

---

### Post by A_M_S on 2009-06-14
> **unutbu said:**
> Wait for it...




Wait for it...





EMACS! hehe

(Install the emacs-snapshot package if you'd like to use ttf fonts.)

thanks.:)
It was necessary 65,7 MB of disk space for emacs.
Why, is Emacs so big?

---

### Post by ibuclaw on 2009-06-14
Emacs is not a standard editor in Linux/Unix systems alike.



For quick fix text editors, **nano** or **vim** do the job just as well, if not better without it.

Regards
Iain

---

### Post by Celauran on 2009-06-14
Emacs is more than a mere text editor. It's practically an OS unto itself.

---

### Post by A_M_S on 2009-06-14
Tnx for the tips, guys! ;)

---

### Post by unutbu on 2009-06-14
Yes, it is quite large.
If hard disk space is an issue, then maybe emacs is not the right editor for you.

However, with modern hard disks getting so large, emacs' size is becoming less and less of an issue.

On the positive side, emacs is extremely powerful.

For a tutorial on how to use emacs, run emacs and type Ctrl-h Ctrl-h t. And to read the manual, Ctrl-h Ctrl-h r.

---

### Post by ibuclaw on 2009-06-14
> **unutbu said:**
> For a tutorial on how to use emacs, type Ctrl-h Ctrl-h t.
And to read the manual, Ctrl-h Ctrl-h r

On that note, meta-sequence commands are restrictive and obfuscated in single mode text editors. :)

---

### Post by camper365 on 2009-06-14
Joe's Own Editor doesn't come by default, but it is really nice. It includes syntax highlighting for shell scripts, c++, etc. and is a lot like nano and vim combined (mostly nano). I agree with you, vim is hard to understand.
If you want a really simple editor, nano is good (you can also start nano with the pico command).

To get joe type:
```
sudo aptitude install joe
```

---

### Post by CatKiller on 2009-06-14
Another vote for nano. It's just a text editor, not a programming environment.

---

### Post by MrWES on 2009-06-14
> **A_M_S said:**
> Hello.

Since i'm not a big fan of vi, i would like to use another cli text editor.

Anyone have any suggestions?

Tnx.

If you're needing to do simple config file editing, nano will be just fine, and you can set nano to the default with this command from the terminal:
```
sudo update-alternatives --config editor

```

Choose option #3 -- nano.

Bill

---

### Post by Iowan on 2009-06-14
Another vote for **nano**. One of my favorite features is the brief command list at the bottom of the screen.

---

### Post by kerry_s on 2009-06-14
i prefer mcedit for mine, removed vim & nano on my install. i have busybox vi setup for when i get vi cravings.

---

### Post by andrew.46 on 2009-06-15
Hi A_M_S,

> **A_M_S said:**
> Hello.Since i'm not a big fan of vi, i would like to use another cli text editor.

I hope you are starting to realise that you have perhaps inadvertently reignited a holy war :-). And of course vim is the answer to your question, just spend a bit more time on it!

Andrew

---

### Post by MrWES on 2009-06-15
> **andrew.46 said:**
> Hi A_M_S,



I hope you are starting to realise that you have perhaps inadvertently reignited a holy war :-). And of course vim is the answer to your question, just spend a bit more time on it!

Andrew

Well, it's not as bad as someone asking how to install a desktop manager on their brand spanking new server install! The earth shakes on that one....

~Bill

---

### Post by ad_267 on 2009-06-15
If you don't like vi, how about vim? (It's vi improved!) :D

Hehe nah, nano is probably more what you're after. Definitely don't touch emacs though! ;)

---

### Post by Mornedhel on 2009-06-15
> **andrew.46 said:**
> I hope you are starting to realise that you have perhaps inadvertently reignited a holy war :-). And of course vim is the answer to your question, just spend a bit more time on it!

No way ! Emacs will fulfill all your needs.

Currently, I have an emacs session running.

I have a LaTeX paper open : emacs has syntax highlighting and handy shortcuts to insert a reference to one of the papers in my BibTeX bibliography, based on any keywords I might enter to describe which one I want to quote. It will also insert stubs for any environments including figure (with caption, label, and float placement). And compile the document in a smart fashion (it will warn me if I have lines that are too long to fit, references that are yet unresolved, and suggest the proper course of action).

I have an ERC (IRC in emacs) session running. When something happens in one of the channels I'm in, the modeline (similar to the status line in GTK apps) will warn me.

I'm reading my mail in Wanderlust, a mail client for emacs. It's integrated with SpamAssassin and handles IMAP really well.

I'm editing my sources list with C-x C-f /sudo::/etc/apt/sources.list . (OK, not really *right now*).
I'm editing a file on a distant server with C-x C-f /ssh:username@host:filename .

Whatever you can think of, emacs has it. Including a vim emulation mode. Games. A calendar. A *psychotherapist*. Syntax highlighting, smart indenting, autocompletion and other IDE features for your favorite programming language. Does vim have an emacs emulation mode ? I didn't think so. Does vim have its own shell and file explorer ? I didn't think so either.

(And yes, it does edit text as well. Also c'mon, modal editing in this day and age ?!)

-- Yours Truly, An Emacs Evangelist

---

### Post by unutbu on 2009-06-15
One simple thing that I love about emacs is Ctrl-s/Ctrl-r.

When you press Ctrl-s and then start typing a few characters, the cursor automatically jumps forward to the first occurrence which matches those characters without you having to press Enter first. Press Ctrl-s again, and the cursor jumps to the next match. 

Ctrl-r works similarly, but searches in reverse (just like in a bash shell).

Just wondering -- does vim have a similar feature?

Please note I'm not interested in fanning a flame war. Just looking for facts.

PS. Thank you for mentioning Wanderlust, Mornedhel. I didn't know about that!

---

