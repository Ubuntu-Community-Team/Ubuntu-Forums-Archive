---
title: "Running a perl script written in windows in Ubuntu"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by martianmartian on 2010-02-28
Dear all.

First of all sorry if anything about this question is obvious. I am a lifelong Windows user and have just decided to take a plunge and install Ubuntu on my computer.

The only problem is that I have a Perl script that I need to run. The Perl script goes to a website, gathers data and saves it in a file. The issue is that I can't get it to work. Within the script there are references to Windows directories for both the input and output files and certain perl libraries. 

e.g. things like:

   $browser = LWP::UserAgent->new( );

      $cookie_jar = HTTP::Cookies::Microsoft->new(

            file => "C:\\Users\\martian\\Cookies\\index.dat",


and:


$dirr="C:\\martian\\files\\grid\\";

open (IN, $dirr . "grid.txt");

open (OUT, ">> " . $dirr .  "results.txt");



Can anyone suggest how I can best change my Perl code to make it run in Ubuntu?

Thanks very much in advance!!

---

### Post by DaithiF on 2010-02-28
Hi, change the paths?  eg.

file => /home/martian/files/somefile

dirr = "/home/martian/grid";

---

### Post by martianmartian on 2010-02-28
> **DaithiF said:**
> Hi, change the paths?  eg.

file => /home/martian/files/somefile

dirr = "/home/martian/grid";


Thanks very much. I really appreciate it.

And do you know anything about how I would fix the Perl directories for libraries like HTTP::Cookies: and LWP::UserAgent?

One more thing. In windows to run the program, I would use the command line to type "perl nameofprogram.pl" Does this work the same way in Ubuntu?

Thanks!!

---

### Post by ptviperz on 2010-02-28
> **martianmartian said:**
> One more thing. In windows to run the program, I would use the command line to type "perl nameofprogram.pl" Does this work the same way in Ubuntu?


You can do it that way, or add
```

/usr/bin/perl

```
to the top of the program then simply,
```

./someprogram.pl

```

Don't forget to chmod +x the program before you run it the first time, this command sets the program as executable

---

### Post by ptviperz on 2010-02-28
> **martianmartian said:**
> And do you know anything about how I would fix the Perl directories for libraries like HTTP::Cookies: and LWP::UserAgent?

Don't you need to install the packages from CPAN? That's about it....very simple to install in Linux

---

### Post by martianmartian on 2010-02-28
> **ptviperz said:**
> Don't you need to install the packages from CPAN? That's about it....very simple to install in Linux

Thanks. I'll have a look at CPAN to see if I can figure it out.

In my script I had to set the directory. It is currently C:\perl. Do you know what I would change that to now in Ubuntu?

Again I really appreciate the help :) Hopefully this won't be as hard as it initially seemed...

---

### Post by ptviperz on 2010-02-28
> **martianmartian said:**
> Thanks. I'll have a look at CPAN to see if I can figure it out.

In my script I had to set the directory. It is currently C:\perl. Do you know what I would change that to now in Ubuntu?

Again I really appreciate the help :) Hopefully this won't be as hard as it initially seemed...

Here is the easy way to install in linux

```
sudo perl -MCPAN -e 'install HTML::Template'
```

Just substitute your packages for HTML::Template

I don't think you need to worry about the path in linux....

---

