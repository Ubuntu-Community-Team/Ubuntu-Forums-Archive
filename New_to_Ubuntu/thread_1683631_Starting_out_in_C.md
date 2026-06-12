---
title: "Starting out in C"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2011-02-07
I start my advanced computing course september, and as I know relatively little more than how to use computers, I've decided to start learning some of the stuff now so as not to get too overwhelmed at the start.

The programming class is the part I know the least about - nothing to be honest, and I know we start with C and C++. I have found some good online tutorials at cprograming.com, which recommends using Code::Blocks. As this is the first step, I want to get it right, so just wondering if you guys agree or whether you think I should use a different compiler/development environment?

Many thanks in advance!

---

### Post by cgroza on 2011-02-07
Codeblocks should be fine, but in the beginning even light weight editors like geany are enough. Many people just use an editor with some good features and g++.

Good luck.

---

### Post by nickleboyblue on 2011-02-07
The absolute best approach for beginners is to avoid IDE's and go for a simple text editor with a compiler.  The IDE's will leave you very confused, and you'll learn some not-so-good programming habits that are not easy to ditch later on.

I suggest gedit and g++.  Write your file in gedit (with appropriate filename extensions, like .cpp for c++ or .c for c).  Once you're done writing your program, compile it using g++.  Type "g++" and follow it with your file's name.  If you're picky about what the compiled program is going to be named, write "-o <executable-name>" afterwards.  Code:

```
g++ <filename> -o <executable-name>
```

That will transform your written code to machine-readable code, which can then be run (if you didn't mess up in your code) by typing:

```
./<executable-name>
```

---

### Post by quadproc on 2011-02-07
> **nickleboyblue said:**
> The absolute best approach for beginners is to avoid IDE's and go for a simple text editor with a compiler. 
Agreed.  I suggest that the first thing to do is to write the K&R program which does nothing more than prints out "Hello, world!".  The entire purpose of this exercise is to make sure that the beginning programmer knows how to use the editor and compiler, and gets to see the minimum that is required in a C program.  Once you are comfortable with this simple exercise then you can start to add features to the program; for example, you could use stdin and stdout to ask for a number, add one to it, and display it.  Then you are truly and well on your way.

quadproc

---

### Post by wojox on 2011-02-07
I agree as well. A compiler and file editor of choice. Also learn [standard C++ library]("http://www.cplusplus.com/reference/").

You installed the build tools:

```
sudo apt-get update; sudo apt-get install build-essential
```

---

### Post by kumar pratyush on 2011-02-07
I'm using text editor for programming. Every time I compile I get an error. It says '%d' expecting 'int *' instead encountered 'int'. Some help??:mad:

---

### Post by lisati on 2011-02-07
> **kumar pratyush said:**
> I'm using text editor for programming. Every time I compile I get an error. It says '%d' expecting 'int *' instead encountered 'int'. Some help??:mad:

An example of the piece of code which triggers this error would be nice.....

---

### Post by liquidxit2 on 2011-02-07
> **nickleboyblue said:**
> The absolute best approach for beginners is to avoid IDE's and go for a simple text editor with a compiler.  The IDE's will leave you very confused, and you'll learn some not-so-good programming habits that are not easy to ditch later on.

I suggest gedit and g++.  Write your file in gedit (with appropriate filename extensions, like .cpp for c++ or .c for c).  Once you're done writing your program, compile it using g++.  Type "g++" and follow it with your file's name.  If you're picky about what the compiled program is going to be named, write "-o <executable-name>" afterwards.  Code:

```
g++ <filename> -o <executable-name>
```That will transform your written code to machine-readable code, which can then be run (if you didn't mess up in your code) by typing:

```
./<executable-name>
```

While I agree the learning curve in eclipse can be somewhat steep, the same could be said for using emacs to code. I prefer to code in simpler editor (e.g. notepad2) or heck even vi, but Ill admit when on my win 7 box I prefer VS2008.

---

### Post by pafufta503 on 2011-02-08
i use gedit and the GNU compiler (GCC).  i have looked at codelite, but IDE's do tend to confuse me.  i keep things simple, of course if you are working on a larger project you might prefer an IDE.

terminal is your friend ; )

---

### Post by jonnny_j22 on 2011-02-08
Cheers for all the advice and encouragement guys, It hadn't even occured to me that simple was best - obvious really! 

As always, a huge thank you to the community!

---

