---
title: "Problems installing Ruby on Rails"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Mila on 2009-04-20
I'm running Ubuntu 8.10 and just tried installing Ruby on Rails. I've gotten to a certain point and then everything stops working. This is what I've done so far:
```
sudo apt-get install ruby-full build-essential

wget http://rubyforge.org/frs/download.php/55066/rubygems-1.3.2.tgz
tar xzvf rubygems-1.3.2.tgz
cd rubygems-1.3.2
sudo ruby setup.rb
sudo ln -s /usr/bin/gem1.8 /usr/bin/gem
```

Everything works fine up until here. But when I try to install rails using RubyGems like so:
```
sudo gem install rails
```

I get the error: *sudo: gems: command not found*.

I have no idea what is going wrong. I haven't gotten any error messages anywhere else.

Help?

---

### Post by yeats on 2009-04-21
So are you following instructions somewhere?

I'm not familiar with this particular program, but I can't help but notice that the error you've posted is different than the command:

> 

```
sudo **gem** install rails
```

I get the error: sudo: **gems**: command not found.

Also, have you tried calling the program with the full path?:

```
sudo /usr/bin/gem install rails
```

Again - I'm not familiar with the process.  If you're following a set of instructions somewhere, link to them, and perhaps someone can guide you in the right direction...

---

### Post by blazemore on 2009-04-21
try
```
sudo chmod +x /usr/bin/**gem**
```

---

### Post by Mila on 2009-04-21
The whole gem/gems thing is a typo. The actual command I typed was: 
```
sudo gem install rails
```

And the error I got was: sudo: gem: command not found.

I tried to chmod like blazemore suggested and I got the error: *chmod: cannot access 'usr/bin/gem': no such file or directory*, which leads me to think that there was a problem installing RubyGems.

Unfortunately I really don't know any other way to go about installing RubyGems since every instruction set insists that installing via apt-get is very not recommended.

I'm following the instructions on the Ruby On Rails wiki for installing on linux here: [http://wiki.rubyonrails.org/getting-started/installation/linux](http://wiki.rubyonrails.org/getting-started/installation/linux)

---

### Post by Tibuda on 2009-04-21
I could not get Rails working with the ubuntu repositories gems in neither Intrepid and Jaunty. I installed it from source too.

Do you get any message when running "sudo ruby setup.rb"?

---

### Post by Mila on 2009-04-21
Nope. No errors. Just the readme.

---

### Post by Tibuda on 2009-04-21
Open a terminal and type
```
cd /usr
find -iname gem*
```
It will search for files starting with "gem" in the /usr directory.

---

### Post by blazemore on 2009-04-21
The command
```
sudo ln -s /usr/bin/gem1.8 /usr/bin/gem
```
Takes an existing file (/usr/bin/gem1.8) and makes a "shortcut" to it as the file /usr/bin/gem.
This means you can use the command "gem" rather than "gem1.8"

Does gem work if you use gem1.8 as a command, rather than just gem?

---

### Post by umuro on 2009-06-09
Would you still have the same problems if you apply the installation steps documented in [http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation](http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation) ?

---

### Post by MikeFlint on 2010-09-09
Blazemore - thanks your suggestion sorted me out  :)

I am running Ubuntu 8.04 (server) so the ubuntu repository had a very old (0.9.4) gem package.  After I removed that I had to install gems from setup.rb in the package and that worked, but failed to build/repair the symbolic link.

Fixing that, and rubygems was back up and running as 1.3.7.

---

### Post by Abonec on 2010-12-12
I have a similar problem with ubuntu 10.10 and gem but a little different difficult:

I installed gem:
sudo apt-get install rubygems

After that I install rails and some other gems via gem:
sudo gem install rails
It seems as correctly installed.

But after that in terminal command 'rails' don't work =(
But in 'gem list' rails is correctly shown
I can't generate controller, start webserver etc because command 'rails' in not work in terminal =(

I found rails in /var/lib/gems/1.8/bin and it seems working, but rails not work in other places 

Please help me

---

