---
title: "variation in command line performance"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by caye on 2009-09-03
each time i enter 
#1/var/bin/perl print "beginner for sure /n"; i get a different response.. 
most of the time the response is nothing, but some of the time it prints
beginner for sure.. what is going on.. 
how could this be is perl turned off..? or what?
ubuntu 9.04  perl 10.5..

---

### Post by Mornedhel on 2009-09-03
> **caye said:**
> each time i enter 
#1/var/bin/perl print "beginner for sure /n"; i get a different response.. 
most of the time the response is nothing, but some of the time it prints
beginner for sure.. what is going on.. 
how could this be is perl turned off..? or what?
ubuntu 9.04  perl 10.5..

OK, first thing I think you meant Perl 5.10. Perl 10 is probably several centuries away in the future.

Your shebang line is weird. Your script probably should look like :

```
#!/usr/bin/perl
print "beginner for sure\n";
```

Run it with "perl script.pl" or just "./script.pl" if you've made it executable.

You seem to be a total beginner in Perl. Ask again here if you have more questions, but be sure to consult the documentation on perldoc.perl.org and the perldocs which are probably installed on your system.

Linux distributions usually depend on Perl for a lot of very basic things, so it's impossible that

---

### Post by caye on 2009-09-03
sorryeee about the shabang error.

I typed which perl and got /usr/bin/perl
I typed #!/usr/bin/perl  print "new user for sure/n";  # on the same line
and return nothing happened.. even after 8 tries.. 

so then I created the split line in my text editor as 
#!/usr/bin/perl 
print "new user for sure/n";

and saved it as mynew.pl into my home directory, and switched to the terminal and 
 typed    mynew.pl  still nothing. printed out. 
d/n forget that two days ago this very stuff worked great?
I reinstalled 5.10 and it installed fine, but the reinstall made perl work for one time, 
after that it would not work.. I have not tried to reinstall again. 
thanks your help.

---

### Post by DaithiF on 2009-09-03
> 
I typed #!/usr/bin/perl  print "new user for sure/n";  # on the same line
and return nothing happened.. even after 8 tries.. 

Hi,
nothing happening is exactly what should happen.  Generally in bash any line starting with # is a comment, and is ignored by the shell.  There is one exception -- when #! occurs at the first line of a file, then its interpreted as a 'shebang', or an instruction as to which command to execute this file with.  At an interactive shell though #! is just a comment, and will be ignored.  Hence your first attempts did nothing.

Your second attempt is on the right track.  A couple of things to check:
1. make sure mynew.pl is executable .. run chmod +x mynew.pl
2. you need to tell bash where myew.pl is, unless it is in a directory which is on your PATH environment variable.  Your home directory is most likely NOT on your path, so you should tell bash you're executing something in the current directory:
./mynew.pl

however, either of these things would have resulted in output to the terminal indicating there was a problem -- permission denied for 1., and command not found for 2.  Was there any output when you entered your command.

please try again, and if it still doesn't work, then post the output of:
cat mynew.pl
and copy/paste the lines from the terminal where you try to run it.

---

### Post by caye on 2009-09-03
Your instructions worked. thanks.  
But I am curious, if the bash shell  symbol # makes a comment.. of every entry.. 
how do you run perl from a command line without bundling the lines of code into a 
perlscript.pl file?   It ran one time or so that way?  must be a way to do it.. and an explaination of why it works
#!/usr/bin/perl   lines of code;
lines of code;
lines of code;
^c
or 

#!/usr/bin/perl lines of code;
#!/usr/bin/perl  lines of code;
#!/usr/bin/perl lines of code;

will either of these work? thanks. I learned a lot from your help..

---

### Post by Mornedhel on 2009-09-04
> **caye said:**
> But I am curious, if the bash shell  symbol # makes a comment.. of every entry.. 
how do you run perl from a command line without bundling the lines of code into a 
perlscript.pl file?   It ran one time or so that way?  must be a way to do it..

I'm not sure I understand what you mean. There are two main ways of writing and executing Perl code : one is to write a .pl script like you did, the other is to run something like :

```
perl -e 'print "something like this\n";'
```

The -e switch means "execute the next argument as if it were Perl code".

> **caye said:**
> #!/usr/bin/perl   lines of code;
lines of code;
lines of code;
^c
or 

#!/usr/bin/perl lines of code;
#!/usr/bin/perl  lines of code;
#!/usr/bin/perl lines of code;

will either of these work? thanks. I learned a lot from your help..

The second one will definitely not work. The first one will work if you just put all lines of code on their separate lines : again, any line starting with # will not be executed as Perl code. The shebang #! line is not even mandatory but allows executing your script without explicitely calling perl on the command line (like ./this.pl).

---

### Post by DaithiF on 2009-09-04
> **caye said:**
> 
how do you run perl from a command line without bundling the lines of code into a 
perlscript.pl file?
either:
```
perl -e 'print "this is a single perl statement/expression\n"'

```or (never really seen this done in practice), but you *could* create whats called a 'here' document, where you tell the shell to pass every from here onward into a command, up until a closing marker ... 
command <<SOMEMARKER
1st line
2nd line
SOMEMARKER
so a perl example:
```
perl <<EOF
print "this is a perl print statement\n";
print "and this is another\n";
EOF

```

and note that, once again, when running interactively from the command line you do not want to have 'shebang'.  And since perl is most likely on your PATH, you can invoke it by just running perl.  No need for /usr/bin/perl (unless you have a messed up PATH :) )

---

