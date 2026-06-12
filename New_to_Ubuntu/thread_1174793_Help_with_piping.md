---
title: "Help with piping |"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by gtr32 on 2009-05-31
I know piping can be a great tool but I can't seem to get it to work. I have used piping for things like grep for a long time but what if I wanted to download a .deb file and pipe it to dpkg?

This doesn't seem to work:

wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) | dpkg -i

Neither does this:

uptime | echo

I must be doing something fundamentally wrong here. I tried to search for an answer but I think I'll get a faster resolution by posting it here. It must be simple but I just can't figure it out.

---

### Post by glennric on 2009-05-31
A pipe takes the stdout from one program in passes it as stdin to the next.  So you have to understand the capabilities and usage of the programs you are piping to and from.

For example, wget by default will write the file you are downloading to a file, and not to stdout.  If you pass "-O -" to wget it will write to stdout.  So in your case
```
wget -O - http://www.skype.com/go/getskype-linux-deb
```
Of course if execute that command you will get a lot of gibberish in your terminal.  The point here, as you desire, is to pipe that to another program's stdin.  Unfortunately dpkg does not accept a file from stdin (as far as I know).  It only accepts a file name as a parameter to the command.

Your second example is rather pointless.  You are trying to pipe the output of "uptime" to "echo".  "uptime" is sending what you want to stdout.  "echo" doesn't accept stdin, and even if it did all it would do is pass the stdout back to stdout.

---

### Post by llamakc on 2009-05-31
> **gtr32 said:**
> I know piping can be a great tool but I can't seem to get it to work. I have used piping for things like grep for a long time but what if I wanted to download a .deb file and pipe it to dpkg?

This doesn't seem to work:

wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) | dpkg -i

Neither does this:

uptime | echo

I must be doing something fundamentally wrong here. I tried to search for an answer but I think I'll get a faster resolution by posting it here. It must be simple but I just can't figure it out.

xargs can be of some help.

```

uptime | xargs echo

```

```

wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) | xargs dpkg -i

```

```

man xargs

```

Of course the dpkg portion requires sudo.

---

### Post by lswb on 2009-05-31
Piping sends the output of the first command to the input of a 2nd command. The 2nd command must be one that looks for and can act on something on its "standard input." In the case of dpkg, it does not recognize anything on it's input, it is controlled solely by options and file names on its command line. OTOH, grep and similar commands DO look at their standard input, which is why something like 

wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) | grep "SearchString"

would. However, it would not search the contents of the downloaded deb file, it would only search for the standard output of the wget command, which is what you see on the terminal screen while and after the wget command runs. Same thing with echo, it is not looking for any standard input, only looking at its command line.

For your dpkg example, you could put 2 separate commands in a script, preferably with additional error checking to deal with a failure by wget to downloadthe complete file. Or if you really need to do the download and install using a single line, something like

wget [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) && dpkg -i getskype-linux-deb

would work. Using the && between the 2 commands ensures that the 2nd won't run unless the 1st completes successfully.

---

### Post by gtr32 on 2009-05-31
Thanks Glenn, that helped. I had thought it might be something like that. Yes, the second example is pointless but I just used it as an example.

So if I wanted to write a script that downloads that skype package and installs it with dpkg, I would have to do two steps:

1) Download the file to temp directory
2) Run 'dpkg -i $TEMP_DIR/skype_package.deb'
3) <optional> 'rm $TEMP_DIR/skype_package.deb'

---

### Post by glennric on 2009-05-31
The suggestion that llamakc gave to use xargs will work.  Just for a little explanation, xargs will accept the stdout from the pipe as its stdin, and will add that as a paramater to the command that follows xarg.  So the wget/xargs/dpkg example will work somewhat nicely (although I think lswb has a better way of working that case).  

The uptime/xargs/echo example is really silly though.  uptime passes the message to stdout, then xargs takes that from the pipe as stdin and turns that into a parameter to echo, which in turn passes that back to stdout.

---

### Post by gtr32 on 2009-05-31
> **glennric said:**
> The suggestion that llamakc gave to use xargs will work.
Yes, tested and it does. It still downloads the file.
> **glennric said:**
> The uptime/xargs/echo example is really silly though.
It's really there just to help me understand. I am trying to get more into Linux now, after spending the last decade or so with Windows. I have used Unix and VAX before so I am not totally new but some things I just haven't used extensively before.

Why I tried 'uptime | echo' was an experiment to pass uptime to an executable as parameters. The exe would then parse it and spit out a different output. Now I can try it with xargs (although I could use awk but this is an experiment for me to get to know Linux more).

---

