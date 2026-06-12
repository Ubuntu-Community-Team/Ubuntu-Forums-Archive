---
title: "Installation for self-extracting binary"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by vwang on 2011-03-03
This is a general question about how to proceed when I get a program folder.
A specific example of this is getting downloading jdk-1_5_0_22.linux-amd64.bin and running it, which produces a folder jdk1.5.0_22 containing bin, include, lib and other folders. The programs I want, like javac, are obviously in jdk1.5.0_22/bin/javac and can be run there, but how do I get javac and the other executables as commands (without having to specify their whole location)?

Question in short:
You have a program folder containing /bin, /lib, /include files. What is the best/correct/standard way to get all the binary files recognised as commands?

Long description of my meak thoughts

The two options I know are:
#1 moving stuff to usr/bin or somewhere where commands are searched for automatically
#2 adding a path to ~/.bashrc

However, I see problems with both solutions, so I am wondering what is the most common approach? 
#1 I'd have to copy jdk1.5.0_22/bin contents to /usr/bin, as well as jdk1.5.0_22/lib to /usr/lib and jdk1.5.0_22/include to /usr/include.
  -Firstly I am unfamiliar with /bin vs /usr/bin vs /usr/local/bin. Which is common for what use? What are the implied differences? Which would I use in this case?
  -Due to my ignorance the same question applies to /usr/include vs /usr/local/include.
  -I am guessing that jdk1.5.0_22/include headers would only be useful to me if I was compiling java from scratch?
  -If I did move all these (rather than copy them) then the demo, sample, man and other trivial items are somewhat stored randomly. This problem is a trifle, but it makes me wonder (if this solution is common) do most experienced users delete this stuff, store it systematically, or just store it?
  -If for some reason I wanted to see what libs javac was dependent on, I could have found them easily in their original location. But now that bin/javac and lib/ are at different places, perhaps I'd have to keep an unchanged jdk1.5.0_22/ for reference. Furthermore, if I wanted to uninstall/remove java it seems the only way would be to hunt down all the files in their different locations, while using the original folder as a checklist.
#2 I'd edit .bashrc like:
PATH=$PATH:$HOME/Downloads/jdk1.5.0_22/bin
export PATH
  -Could I just add paths for each new program folder I get? E.g.:
PATH2=$PATH:$HOME/Downloads/eclipse/bin
export PATH2
  -Does that work? Is this an elegant solution, or am I unknowingly treading on the 'dark side'?

Thanks.

---

