---
title: "C++ programming"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-10
I am interested in learning to program, and I got "C++ for Dummies".  The author talks about using Dev C++.  So I googled it and it appears that its meant to run on Win, I guess.  Is there something similar or better than Dev C++ for Linux?  Maybe I'm just missing something or misunderstand what I'm looking for.  Any help is appreciated. Thanks!

---

### Post by Dark Aspect on 2009-08-10
> **zer010 said:**
> I am interested in learning to program, and I got "C++ for Dummies".  The author talks about using Dev C++.  So I googled it and it appears that its meant to run on Win, I guess.  Is there something similar or better than Dev C++ for Linux?  Maybe I'm just missing something or misunderstand what I'm looking for.  Any help is appreciated. Thanks!

You can configure [eclipse]("http://www.eclipse.org/") to use a C/C++ compiler like [gcc]("http://gcc.gnu.org/") with a plugin to give gcc a gui. Since to my knowledge gcc is command line only.

---

### Post by saidinesh5 on 2009-08-10
eclipse might be too heavy for you, if you are a beginner: 
instead try 

Geany  ([http://www.geany.org/](http://www.geany.org/))

or 

Code::blocks

out.
both are available in the synaptic package manager, so feel free to check both of them out and find out what fits you best.

---

### Post by Dark Aspect on 2009-08-11
> **saidinesh5 said:**
> eclipse might be too heavy for you, if you are a beginner

True, I mostly use eclipse for an SVN gui - lol

---

### Post by colau on 2009-08-11
> **zer010 said:**
> I am interested in learning to program, and I got "C++ for Dummies".  The author talks about using Dev C++.  So I googled it and it appears that its meant to run on Win, I guess.  Is there something similar or better than Dev C++ for Linux?  Maybe I'm just missing something or misunderstand what I'm looking for.  Any help is appreciated. Thanks!
[Netbeans]("http://www.netbeans.org/downloads/")

---

### Post by credobyte on 2009-08-11
IMO, Geany - simplicity and speed is all you'll ever need :)

---

### Post by jrox717 on 2009-08-11
also, if you're interested in a really good tutorial, I've been using [http://www.learncpp.com/](http://www.learncpp.com/)

---

### Post by issih on 2009-08-11
Whilst you are learning, all you will need is a decent text editor with source markup highlighting (almost any linux text editor will do, even gedit) and a compiler (just install the build essential package and learn about g++)

Technically, that is all you will ever "need", but once you get into having large programs more features can be useful, but its a matter of personal taste 

Hope that helps

---

### Post by purplearcanist on 2009-08-11
> **zer010 said:**
> I am interested in learning to program, and I got "C++ for Dummies".  The author talks about using Dev C++.  So I googled it and it appears that its meant to run on Win, I guess.  Is there something similar or better than Dev C++ for Linux?  Maybe I'm just missing something or misunderstand what I'm looking for.  Any help is appreciated. Thanks!

I would recommend learning Java first.

---

### Post by cmay on 2009-08-11
Dear OP. 

while your Problem is merely to find a suitable IDE you will get some suggestions along the way the way to choose any other language instead. 
Do not fall for this advise because to Learn to think for one self and decide for one self just as y*ou already did *is very important. 

besides that there will always be some articel that says the language others suggested is not good to begin with like as example this.

from this article : [http://catb.org/~esr/faqs/hacker-howto.html]("http://catb.org/%7Eesr/faqs/hacker-howto.html")
> 
I used to recommend Java as a good language to learn early, but this critique has changed my mind 
(search for “The Pitfalls of Java as a First Programming Language” within it). 
A hacker cannot, as they devastatingly put it “approach problem-solving like a plumber in a hardware store”;
 you have to know what the components actually do. Now I think it is probably best to learn C and Lisp first, then Java.
as you can see things also sometimes change even coming from the same person. 


to adress the original topic. 
as for the IDE i can suggest codeblocks and geany and also to learn from the book and some small online tutorials as well. 
i learn c as the first language and i used devcpp once. its dead as a project and there are far better options in linux as is right now. 

be sure to find a good c++ forum to ask for help when ever you get stuck and good luck :)

---

### Post by Christmas on 2009-08-11
There are plenty IDEs for C++ out there, and the one that resembles Dev-C++ mostly is Code::Blocks. Have a look at Emacs, Vim or Kate too. You can run Dev-C++ through Wine if you really want to, but there are many native alternatives out there. Emacs is my favourite.

---

### Post by arochester on 2009-08-11
Full Circle Magazine did a series about programing in C on Ubuntu. Start here: [http://fullcirclemagazine.org/2008/09/26/issue-17-out-now/](http://fullcirclemagazine.org/2008/09/26/issue-17-out-now/)

---

### Post by cmay on 2009-08-11
here is a link for a c++ programming forum as well.- [http://cboard.cprogramming.com/cplusplus-programming/](http://cboard.cprogramming.com/cplusplus-programming/)

there is a tutorial on the site which is easy to read up on while you study your book. in case you need to ask something the forum is good i think,.

---

### Post by WRDN on 2009-08-11
If you're just starting out, then I would recommend using a standard text editor with colour highlighting, not an IDE. Then, compile the applications from the Terminal. I would recommend this as I've found it teaches you much more than simply clicking the Build button in an IDE. The Linux IDE's mentioned (Netbeans, Code::Blocks, Eclipse etc) use the G++ compiler by default (G++ standard for GNU C++ Compiler while GCC is the GNU C Compiler). It's best, in my opinion, to start at a lower level, working with g++ directly, and once you understand how it works, switch to an IDE.
If you wish to use an IDE now, I would recommend Code::Blocks or NetBeans).

---

### Post by Terl on 2009-08-11
I agree with WRDN, Code Blocks is a great choice if you need an IDE for your C++.  It is available through synaptic as well.

I agree also that when starting out it is best to just use a text editor (I am old school and use vim) until you get used to the language's syntax.  Many IDE's prefill a lot for you and often you spend as much time learning the IDE as you do the programming language.  Just some things to think about I guess... :)

---

### Post by zer010 on 2009-08-11
Thanks so much for the help and opinions!  So many great suggestions! I think I'll try out Code Blocks,  but as an IDE "prefills" code, that wouldn't be very helpful in actual learning.  Any great text editors I should look at? Terminal based would be nice.  Program and terminal practice at the same time would be ideal.

---

### Post by Terl on 2009-08-11
> **zer010 said:**
> Thanks so much for the help and opinions!  So many great suggestions! I think I'll try out Code Blocks,  but as an IDE "prefills" code, that wouldn't be very helpful in actual learning.  Any great text editors I should look at? Terminal based would be nice.  Program and terminal practice at the same time would be ideal.

If you want terminal based you can't go wrong with the classic vi or vim :)   You could also install emacs.

I just use the graphical one, gedit, that comes with Ubuntu for most of my practices.  It works just fine.  I have been learning C.

---

### Post by zer010 on 2009-08-14
Well, I am going through the guide [jrox717]("http://ubuntuforums.org/member.php?u=802510") linked to, and it is making learning C++ much easier than I anticipated. I'm not very far into it yet, but it's a great guide.  I haven't really been using the "Dummies" book, as it is geared so heavily towards Win, and Dev C++.  I did get Code::Blocks, but I'm not using it yet.  So far I'm doing my coding in gedit, and it's working out well.  I tried vim, but at first glance I can't really figure it out yet.  I'm doing all my compiling from the terminal using g++.  So far so good.  Thanks everyone for their advice!  So helpful! :)*Thumbs up*(no emoticon for a thumbs up or down).  I guess for now, I'm going to mark this one SOLVED.  Thanks again, everyone!

---

