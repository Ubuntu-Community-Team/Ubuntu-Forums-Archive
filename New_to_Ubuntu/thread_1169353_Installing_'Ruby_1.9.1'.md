---
title: "Installing 'Ruby 1.9.1'"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by JasonInferno on 2009-05-25
Hello everyone.

I have recently downloaded the source code for 'Ruby 1.9.1' and tried to install it. I have entered the following:

```
sudo apt-get install ruby1.9.1
```It installed fine, but I cannot seem to find it anywhere.

Please take into note that I have only begun using Ubuntu about 1 day ago and have previously installed 'Ruby 1.9.1' on Windows via installer. I've also never compiled source code.

If anyone can help me it would be greatly appreciated. :)

**   -Jason Bates**

---

### Post by el-mar01 on 2009-05-25
Have you tried typing in "ruby" into the CLI ??

---

### Post by ad_267 on 2009-05-25
What are you expecting to find?

You can run ruby scripts with "ruby filename.rb"

---

### Post by JasonInferno on 2009-05-25
I'm sorry, but I'm not so sure as to what a CLI is, el-mar. Do you mean the Terminal?

Also ad_267, I'm expecting to install Ruby. I installed it on Windows XP and it had a folder of where I could run a program to code Ruby. I'm not sure if Linux Ubuntu does this, but if I'm to do something else, just tell me and elaborate. Remember that I'm a complete newbie to Linux, let alone Ubuntu. >_>

---

### Post by ad_267 on 2009-05-25
You have installed ruby. Ruby isn't some graphical application, it's an interpreter that runs Ruby scripts. I'm not sure what you mean by "a folder of where I could run a program to code Ruby".

You can use any text editor to write Ruby code, for example gedit which comes with Ubuntu by default. You can save this with the extension .rb and put the first line as "#!/usr/bin/env ruby". That line tells your shell to run the script with ruby. Then to run your script you open up a terminal (yes same as CLI) and browse to the directory where your script is and run "./scriptname.rb"

For example:

Open up gedit with Applications - Accessories - Text Editor. Create a file with the following code:
```
#!/usr/bin/env ruby

puts "Hello World!"
```

Save the file in your home directory as "hello.rb". 

Go to applications - Accessories - Terminal.

Run "chmod a+x hello.rb" to make your script executable. Then run "./hello.rb"

You can also run the script with "ruby hello.rb", which doesn't require the script to be executable.

---

### Post by JasonInferno on 2009-05-26
Erm... I know how to code in 'Ruby' and run script files. Durr. I never asked for coding help. I asked for help in running 'Ruby' before I realised it was just an interpreter. I knew you could code it in Notepad/Text Editor, I just wondered why there was nothing in the **Applications **folder, like Windows. It's obvious that Windows and Linux Ubuntu run completely differently, the fact that Linux's version of 'Ruby' was completely different to Windows's wasn't too obvious. **>_>**

As by 'a folder of which I could run 'Ruby'', I meant to click **Start > All Programs > Ruby 1.9.1 > SciTE**,run **SciTE **and begin coding. Now that I know it runs different to the Win version, I can code in peace and close this thread.

---

### Post by syielic on 2009-05-31
> **JasonInferno said:**
> Hello everyone.

I have recently downloaded the source code for 'Ruby 1.9.1' and tried to install it. I have entered the following:

```
sudo apt-get install ruby1.9.1
```It installed fine, but I cannot seem to find it anywhere.

Please take into note that I have only begun using Ubuntu about 1 day ago and have previously installed 'Ruby 1.9.1' on Windows via installer. I've also never compiled source code.

If anyone can help me it would be greatly appreciated. :)

**   -Jason Bates**

I need to finish my git hub repos and help people out more.

Install ruby 1.9.1 from source + rails with this code below. It will install your ruby 1.9.1 in a folder called "rubysrc" in your home folder.

For a rails application just open up a terminal and enter in "mkdir rubyapps" and it will create a folder in your home folder. Then just do this in your terminal, "cd ~/rubyapps/" then "rails applicationname". Good luck. 

### Installing Ruby 1.9.1
sudo apt-get install -y build-essential libssl-dev libreadline5 libreadline5-dev zlib1g zlib1g-dev make 
mkdir ~/rubysrc && cd ~/rubysrc
wget [ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.1-p0.tar.gz](ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.1-p0.tar.gz)
tar xvfz ruby-1.9.1-p0.tar.gz
cd ruby-1.9.1-p0
./configure
sudo make
sudo make install
cd ~


#### Installing Ruby Gems
sudo gem update --system
sudo gem install rails


#### Installing SQLite Essentials
sudo apt-get -y install sqlite3 libsqlite3-dev
sudo gem install sqlite3-ruby

---

### Post by Tibuda on 2009-06-01
> **JasonInferno said:**
> Erm... I know how to code in 'Ruby' and run script files. Durr. I never asked for coding help. I asked for help in running 'Ruby' before I realised it was just an interpreter. I knew you could code it in Notepad/Text Editor, I just wondered why there was nothing in the **Applications **folder, like Windows. It's obvious that Windows and Linux Ubuntu run completely differently, the fact that Linux's version of 'Ruby' was completely different to Windows's wasn't too obvious. **>_>**

As by 'a folder of which I could run 'Ruby'', I meant to click **Start > All Programs > Ruby 1.9.1 > SciTE**,run **SciTE **and begin coding. Now that I know it runs different to the Win version, I can code in peace and close this thread.

Because you already got a powerful and extensible application in your Ubuntu: Gedit. Start it from Applications > Accessories > Text editor.

---

### Post by ad_267 on 2009-06-01
Yeah SciTE is just a text editor. That's one of the great things about Linux, everything you install doesn't come with unnecessary crap you don't need.

---

### Post by Tibuda on 2009-06-01
If you really want to use scite, you can install it from the scite package in synaptic/apt.

---

### Post by syielic on 2009-06-02
Why use scite when you can use Vim! ;)

---

### Post by ad_267 on 2009-06-02
> **syielic said:**
> Why use scite when you can use Vim! ;)

Too true.

---

### Post by Bjoern on 2009-07-06
> ### Installing Ruby 1.9.1
...
sudo make install


Just wondering: wouldn't I also need something to tell Ubuntu that Ruby 1.9.1 is installed? Otherwise some dependencies might install the real ruby1.9 package and some kind of mess could ensue?

---

### Post by juanoleso on 2009-07-06
> **Bjoern said:**
> Just wondering: wouldn't I also need something to tell Ubuntu that Ruby 1.9.1 is installed? Otherwise some dependencies might install the real ruby1.9 package and some kind of mess could ensue?

Whenever I build from source, I use checkinstall to create a .deb.  Apt then has more of a chance of recognizing what has been installed.

---

