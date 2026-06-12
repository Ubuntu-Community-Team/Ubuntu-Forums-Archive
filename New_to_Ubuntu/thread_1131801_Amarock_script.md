---
title: "Amarock script"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by studiodude on 2009-04-21
I&#7743; trying to run an amarock script but its calling for one of 3 things to be installed, RubyGTK is one of them and i have downloaded the source and extracted it to my home/marc folder.
Following instructions in the "read me" i opened a terminal and changed (cd)to the correct folder.  Im at the point where i need to create the Makefile and using the commands given:-

3. create Makefile
       $ ruby extconf.rb
       If gtk-config is installed with other name (ex. gtk12-config), 
       $ ruby extconf.rb <other name>

so i put into the terminal 

ruby extconf.rb

it returns - 

extconf.rb:5:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:5

so i put in to the terminal

ruby extconf.rb gtk-config.cygwin

as that is the only other file apart from some other text files and folders in that particular directory, and it returns the same.
 
extconf.rb:5:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:5

so i trim it to:
ruby extconf.rb gtk-config

as in the instructions in step 3

same result

At which point I am stuck - can anyone shed any light into what i am doing wrong please?

---

### Post by amingv on 2009-04-21
You shouldn't need to install it from source unless you have a particular reason to do so.

Maybe try

```
sudo aptitude install libgtk2-ruby
```

---

### Post by finer recliner on 2009-04-21
rather than installing from source, try installing the package from the ubuntu repository:

```
sudo apt-get install libgtk2-ruby
```

(i think thats the package you want)


EDIT: oops, looks like amingv beat me to it.

---

### Post by studiodude on 2009-04-21
Thanks guys, i looked in the repository but it wasnt there and I&#7743; not exactly sure how you go about finding the exact thing to look for in the terminal,

i get the

 sudo apt-get install - bit but dont know how you find out about the

 libgtk2-ruby - bit.  There certainly was nothing on the site I downloaded the source code from cos I looked and it looked like that was the official site for it.

Is there something i need to know to find these things out?, I can understand having a stab at say - sudo apt-get install amarock - but i´d never have guessed  "libgtk2-ruby" - where do you get that bit from?

sudo apt-get install libgtk2-ruby worked by the way, thanks, I have it installed now.

---

### Post by finer recliner on 2009-04-21
glad it worked for you :)

yes, some package names are easy to figure out, and some aren't. For those that are not obvious, either seach/install using synaptic (system > administration > synaptic), or search online: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then use apt-get in the terminal again.

---

### Post by studiodude on 2009-04-22
Thanks for that link - another gem for my faves. :-)

---

