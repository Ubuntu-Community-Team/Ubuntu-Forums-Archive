---
title: "Noobish Question"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Tystick86 on 2011-02-16
Hello everyone hope all is well. So after I made the switch to Linux I have been studying command line tools and ruby on rails because whats the point of having a linux box if you can't pound away on a keyboard in a terminal...any way in my studies I have run into a question which I could not possibly ask Google because its hard to search for characters like - in Google.

Does any one know why some options in command line tools have one dash like ls -a and others have two like rails console --sandbox?

Its been puzzling me any help would be appreciated thank you.

---

### Post by TeoBigusGeekus on 2011-02-16
[http://ubuntuforums.org/showthread.php?t=1652811]("http://ubuntuforums.org/showthread.php?t=1652811")

---

### Post by kn0w-b1nary on 2011-02-16
I'm no expert but I've noticed that one dash is followed by one letter, while two dashes are followed by a word.

Hope this helps!

---

### Post by DanneStrat on 2011-02-16
> **Tystick86 said:**
> Hello everyone hope all is well. So after I made the switch to Linux I have been studying command line tools and ruby on rails because whats the point of having a linux box if you can't pound away on a keyboard in a terminal...any way in my studies I have run into a question which I could not possibly ask Google because its hard to search for characters like - in Google.

Does any one know why some options in command line tools have one dash like ls -a and others have two like rails console --sandbox?

Its been puzzling me any help would be appreciated thank you.

Hi!

It is two ways to specify an argument.

If I for example would like

to make a symbolic link, I would do

```
ln -s
```

but if I do

```
ln --symbolic
```

it would be the same thing.

If you have a terminal application that

you want to use but don't know

the arguments to use you can use the "man" command.

An example:

```
man ls
```

would show you the manual

for the "ls" command and there you

will also find the available arguments.

---

### Post by Tystick86 on 2011-02-16
Right on that was one of those not so important but still nagging at the deeper levels of brain questions so thank you for your help everyone :)

---

### Post by Old *ix Geek on 2011-02-16
Back in the day--the "command line only" day--when I started on UNIX (mid-1980s), the single dash was the ONLY way to specify an argument. The double dash thing is newer--and I don't use it! I still stick with what I'm most comfortable with.

Note, too, that the original method [single dash] allows for combining of command line arguments, while the double dash obviously cannot. For example, if a command has options called -a -b -c and -d, you can type that as **command -a -b -c -d** OR **command -abcd**. The latter is obviously easier than the former. Yet another reason I stick to the old method.

---

