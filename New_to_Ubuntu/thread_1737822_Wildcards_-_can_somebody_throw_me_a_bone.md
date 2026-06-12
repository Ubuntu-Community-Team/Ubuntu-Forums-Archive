---
title: "Wildcards - can somebody throw me a bone?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-04-23
Hi,

I'm working on beefing up my understanding/ skills with wildcards. I have a book/ books that I'm following but I have two questions I'd love to learn the answers to. Well, three questions, really - but the last one is sort of tied to the others. What follows kinda goes off in a couple directions but the crux of my curiosity is about wildcards.

1) Can wildcards be used with "ls" to expand the results of a complex, multi level directory - and the result be shown in sections and subsections (so it's not just all jumbled together)? As an aside to that - I assume I can also pipe the result off of my terminal window by adding something like " | less" ? Maybe even save it in a file with something like " > filename.txt"?

2) Same as the first question only with the comand "mkdir". The result being to create a large directory with multiple levels using one, short, simple command? Even a very complex directory containing hundreds or even thousands of folders and many levels?

3) Is there a way to find out answers to questions like the above through information already in bash (method as much as means)? In a nutshell, how to investigate what commands work together or not.

Now some of the books I have mention these things but they either mention them only in passing or the way they explain it leaves me confused. One book, in particular, is great for leading me through exercises but comes up very short on exploring possibilities and explaining syntax. Another is very in depth but uses terminology that makes it impossible for me to grasp. I can't even tell you how many times I've been over some of the same material and I'm still stuck. I thought a few practical examples might help me.

Thanks a bunch in advance. Hope these aren't too broad or big of questions. If it's too much, I understand. I appreciate anything you can offer.

Thank you.
:)

---

### Post by IHeequ5i on 2011-04-23
#1 - yes.  Use
```
ls -R > files.txt
```

The -R switch makes it recurse through all subdirectories. If you want to display it on the screen, you can (as you assume) use:

```
ls -R | less
```

#2 - not sure exactly what you're wanting to do here. More details please?

#3 - There's a couple things you can do:

```
man ls
```

or 

```
ls --help
```

man will work for the vast majority (if not all) of the terminal commands. The --help (note that it is TWO dashes) switch works on many of them. A lot of times using "/?" as a switch will produce a message that tells you the correct syntax for getting more information.

Hope this helps.

---

### Post by heyandy889 on 2011-04-23
> **Doomspark said:**
> #2 - not sure exactly what you're wanting to do here. More details please?Thinking the poster is wondering about a way to make a complex folder structure with one command. I've read that it's possible, but I don't know how. For example
```

nate@nate-laptop:~/myfolder$ ls -R
 .
..
onlyonefile
nate@nate-laptop:~/myfolder$ [insert special mkdir command here]
nate@nate-laptop:~/myfolder$ ls -R
.:
onlyonefile

./folder1:

./folder2:

./folder2/folder2:

./folder3

```

---

### Post by ClientAlive on 2011-04-24
> **Doomspark said:**
> #1 - yes.  Use
```
ls -R > files.txt
```

The -R switch makes it recurse through all subdirectories. If you want to display it on the screen, you can (as you assume) use:

```
ls -R | less
```

#2 - not sure exactly what you're wanting to do here. More details please?

#3 - There's a couple things you can do:

```
man ls
```

or 

```
ls --help
```

man will work for the vast majority (if not all) of the terminal commands. The --help (note that it is TWO dashes) switch works on many of them. A lot of times using "/?" as a switch will produce a message that tells you the correct syntax for getting more information.

Hope this helps.


Oh, ok. Well, on #2 - it occurred to me that if a person were familiar enough with bash and he knew wildcards and special characters well - that, that person could basically write a pretty succinct line of code that would make a whole directory system lickedie split! I mean a big, complicated one. Anything you could picture a map of in your mind.

For instance: lets say you wanted to house 20, 000 varying media files that were stored somewhere just all lumped together and you needed a directory system for them. To organize them out propperly. Lets also say that they consisted of audio, video and graphics files; and, in addition to that, each of the respective types had several different file types. Finally, lets say you also wanted to group them according to band, or genre, or project - respectively. So you want them to all have a nice little home to live in and move them on in real nice like and you want to minimize the amount of work you need to do to accomplish this.

I would assume something, even as complex as that, could be accomplished with as little as 3 or 4 pieces of code strung together with "; " if you were using all your wildcards right and the full use of the special characters like back quote and parenthesis, etc. (Yes, while I was away I found a great little two page article on wildcards and the special characters - very simple and informative).

So then, maybe you'd have two or three pieces of code strung together for making the directory structure and finish it with an ls of the kind that showed you everything that had been done. Them maybe a couple more pieces of code strung together to move the files over into the folders. Within a very short, easy time you'd accomplish a tremendous amount.

now I hope I'm not off base here. Somehow I'd gotten the idea that code can be looked at similar to algebra in the way algebra has and order of operations and you can use that to write complex expressions. Please correct me if I'm off track here.

By the way (and I'm chuckling at this now) I did find a way to use wildcards to make ls list the contents of 10 directories each containing 26 directories from the main parent directory but I can't recall what I did now. Lol.

> **heyandy889 said:**
> Thinking the poster is wondering about a way to make a complex folder structure with one command. I've read that it's possible, but I don't know how. For example
```

nate@nate-laptop:~/myfolder$ ls -R
 .
..
onlyonefile
nate@nate-laptop:~/myfolder$ [insert special mkdir command here]
nate@nate-laptop:~/myfolder$ ls -R
.:
onlyonefile

./folder1:

./folder2:

./folder2/folder2:

./folder3

```


Yes. I thought that I could employ wildcards in both the naming/ creation and placement of the folders. for naming/ creating it is "mkdir" and for placement it is "cd". After reading about back quote I'm thinking it could really give you the power to do some damage! Not sure I have a great understanding of back quote yet until I try some things. Only that it seemed to me that using back quote could give you a power with code analogous to parenthesis and exponents in algebra. Sort of like, code within code. That plus wildcards should give you all the power you need to pull off incredible feats with just a few strokes of the keyboard. :D

What do you think guys?

---

### Post by ClientAlive on 2011-04-26
```
mkdir dir{1..12}{a..l}_music; ls
```

111 folders. Albeit just lumped right there in one space.

```
mkdir myfolders{1..1000}{a..z}_whatever; ls
```

How many does that make?

Now to figure out how to nest . . . (nest?) the folders. Or to make them be created in a (heirarchy? Structure?).
:)

---

### Post by nothingspecial on 2011-04-26
If you are trying to do what I think you are trying to do you just need mkdir's -p argument.


```
ns@netbook:~/test$ mkdir -p {Music,Videos,Books}/{A..Z}
ns@netbook:~/test$ ls
Books  Music  Videos
ns@netbook:~/test$ ls Books/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Music/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Videos/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
```

The -p option creates the parent directory if it doesn't exist.

---

### Post by ClientAlive on 2011-04-26
> **nothingspecial said:**
> If you are trying to do what I think you are trying to do you just need mkdir's -p argument.


```
ns@netbook:~/test$ mkdir -p {Music,Videos,Books}/{A..Z}
ns@netbook:~/test$ ls
Books  Music  Videos
ns@netbook:~/test$ ls Books/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Music/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Videos/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
```

The -p option creates the parent directory if it doesn't exist.


Yeah. Well, I'm just playing with possibilities as a learning exercise right now. I have a place I made on my system: "/home/user/cliPlaygrounds/Experimental". I made if for just that purpose and theres even other "playgrounds" in there with directories inside them. So I have stuff to manipulate around with various commands for practice.

I tried to use that -p option before but guess I didn't get it right. Then I, well I guess I just learned what expansion means - if nothing else. I don't actually need this huge directory for anything. Just trying to learn.

Well, so I don't really know what happened or why but I just took that stuff a lil' but further  :)  freaked my computer out. Thought I lost the thing. No folders were ultimately created, it just ran like mad trying to create them for about 3 or 4 min then froze up a little. Freaked me out! lmfao!

Guess I didn't realize what I was asking the thing to do. There's about 30 gig of space left on this thing though so I don't think its a space thing. Whatever it is it's something else. Free mem being overloaded or something. I don't know.

So, I'm sure your curious. What is it I did? Ok, I'll tell ya' But, kids! Don't try this at home . . .

First it was:

```
mkdir dir{1..1000}(A..Z} dir{1..1000}{A..Z}/dir{1..1000}{A..Z} dir{1..1000}{A..Z}/dir{1..1000}{A..Z}/dir{1..1000}{A..Z}
```

Holy cow that was too many folders! It ran for about 5 sec then the terminal window almost immediately closed and that was that.

So I though, well that was too many. I'll just reduce that number a little and be golden!

```
mkdir dir{1..100}(A..Z} dir{1..100}{A..Z}/dir{1..100}{A..Z} dir{1..100}{A..Z}/dir{1..100}{A..Z}/dir{1..100}{A..Z}
```

That got me the reaction I described above.

I need to figure out why that's the case. Why I got that reaction and go back to the drawing board. I'm sure it's that I'm writing very inefficient code. Ugly code. I'll try and learn better than.
:)

Thanks for letting me share guys and for feedback. You help me learn you know.:)

---

### Post by nothingspecial on 2011-04-26
:shock:You were trying to make 100,000 empty directories

---

### Post by timothy48342 on 2011-04-26
> **nothingspecial said:**
> :shock:You were trying to make 100,000 empty directories

If I am understanding...
Wouldn't the command:
```
 mkdir dir{1..100}{A..Z}
```...make 2600 empty folders and if that's true then doing that 3 levels deep would be 2600 cubed or about 17 billion of them.
Try:
```
mkdir dir{1..2}{A..B} dir{1..2}{A..B}/dir{1..2}{A..B}
```...and see what you get. I expect you'll get 4 main folders each containing 4 more.
I'm going to go try it myself now.
--timothy48342

---

### Post by nothingspecial on 2011-04-26
You are right

---

### Post by timothy48342 on 2011-04-26
By the way, the "find" command with no args makes it real easy to see just what your directory tree structure looks like. Better than any ls args, anyway.
Like this:
```
ubuntu@ubuntu:~/Documents$ mkdir upper{1..2}{a..b} upper{1..2}{a..b}/lower{1..2}{a..b}
ubuntu@ubuntu:~/Documents$ find
.
./upper2b
./upper2b/lower2b
./upper2b/lower2a
./upper2b/lower1b
./upper2b/lower1a
./upper2a
./upper2a/lower2b
./upper2a/lower2a
./upper2a/lower1b
./upper2a/lower1a
./upper1b
./upper1b/lower2b
./upper1b/lower2a
./upper1b/lower1b
./upper1b/lower1a
./upper1a
./upper1a/lower2b
./upper1a/lower2a
./upper1a/lower1b
./upper1a/lower1a
```

---

### Post by nothingspecial on 2011-04-26
No wonder the computer nearly blew up

---

### Post by ClientAlive on 2011-04-26
> **timothy48342 said:**
> If I am understanding...
Wouldn't the command:
```
 mkdir dir{1..100}{A..Z}
```...make 2600 empty folders and if that's true then doing that 3 levels deep would be 2600 cubed or about 17 billion of them.
Try:
```
mkdir dir{1..2}{A..B} dir{1..2}{A..B}/dir{1..2}{A..B}
```...and see what you get. I expect you'll get 4 main folders each containing 4 more.
I'm going to go try it myself now.
--timothy48342


17 BILLION! Oh-My-God! I tried to make 17 billion folders on my computer?

I don't think I mentioned it before; but, before all that, I did run a smaller test that worked.

```
mkdir dir{0..9}{a..j} dir{0..9}{a..j}/dir{0..9}{a..j}
```

I "cd"ed into some of those and saw that it works then "rm -r"ed them (deleted them). I just thought it was funny to take this thing to the next level and see what happened. I didn't think I was asking for 17 billion!

I suppose, now, if I use something like that in the future, I'll use it for a practical purpose - for something I actually need the directories for. I am gonna keep learning about better ways to do it though - to do all kinds for things (not just "mkdir").

Now I can move on in my book though cause I get the concept of something they were trying to explain.

> **nothingspecial said:**
> If you are trying to do what I think you are trying to do you just need mkdir's -p argument.


```
ns@netbook:~/test$ mkdir -p {Music,Videos,Books}/{A..Z}
ns@netbook:~/test$ ls
Books  Music  Videos
ns@netbook:~/test$ ls Books/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Music/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
ns@netbook:~/test$ ls Videos/
A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
```

The -p option creates the parent directory if it doesn't exist.


I'm not sure if I can get more then one level out of that. I'll have to fiddle around with it and see what I can do with it. With the other method I could technically get a many levels as I wanted. Granted they would all be uniform with the way I've been doing it but I'm sure building something with specific and unique directories within it is possible.

:D

---

