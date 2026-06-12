---
title: "How to automatically run rails app at startup"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by anotherlinuxnewbie on 2010-06-19
I have ruby and rails installed, and my app ([tracks]("http://getontracks.org/")) works fine when I start it from the terminal window with 
```
script/server -e production 
```
(i.e., my browser brings up the tracks app page when I enter the url: [http://192.168.0.46:3000](http://192.168.0.46:3000)).  I tried putting this command in  /etc/init.d/rc.local like this:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
	        [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		ES=$?
		[ "$VERBOSE" != no ] && log_end_msg $ES
		return $ES
	fi
~/tracks/script/server -e production
}
```
...

but when I restart my server is not running (and this I know because [http://192.168.0.46:3000](http://192.168.0.46:3000) gives me a "could not connect" in my browser).

All assistance will be greatly appreciated.  Thank you.

---

### Post by lkjoel on 2010-06-19
Once, gnome-panel wouldn't load, so I made a link to it on /boot. It worked.

So I would suggest you should put a link to it on /boot

---

### Post by anotherlinuxnewbie on 2010-06-19
I tried putting the command in a file, tracks.sh, in /home/mylogin/tracks/, and I ran sudo chmod +x tracks.sh.  It looks like this: 

```
#!/bin/sh
/home/jenko/tracks/script/server -e production
``` When I look at its properties it shows it's executable, but now when I try and run it (the tracks.sh file), I"m getting a ruby/rails error:

 ```
../config/../vendor/rails/railties/lib/rails/vendor_gem_source_index.rb:1:in `require': no such file to load -- rubygems (LoadError)
```

So it looks like there's something about the pathing that's screwed up when I run it from an executable file.  :(

---

### Post by lkjoel on 2010-06-20
Do you have the latest version installed?

---

### Post by anotherlinuxnewbie on 2010-06-20
Ubuntu: 10.04
Ruby: 1.8.7 patch 174
rails: 2.3.8

---

### Post by anotherlinuxnewbie on 2010-06-20
We're getting close!  

I can now run the script, track.sh, from the terminal window, and it works as long as I DON'T use "sudo" in front of it.  And that's because the pathing is correct for my login id ("jenko") but not, evidently, for "root".  So now I just have to figure out how to run the script as "jenko" when it's run automatically.

Thank you for your support!

---

### Post by anotherlinuxnewbie on 2010-06-20
More info:

I tried this from the terminal window:

```
sudo -u jenko sh tracks.sh
```

thinking that this would run the script as "jenko", and thus have "jenko"'s path.  But it doesn't (have "jenko"'s path, that is).  I put "echo $PATH" in tracks.sh, and when I run the above, I don't get "jenko"'s path, just the normal root path (which doesn't contain any of the ruby or rails paths).

So what I really need is to run it automatically with "jenko"'s path.  Any ideas?

---

### Post by anotherlinuxnewbie on 2010-06-20
alright, I got the script working, and it even works from /etc/rc.local.  Almost.  Here's the /etc/rc.local:

```
#!/bin/sh -e

sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh > /home/jenko/rclocal_executed

exit 0
```

The key to getting it running right was the "PATH=/...", which is the path for jenko. (And I put the "> /home/jenko/rclocal_executed" in to see what's happening.) 
 
Now, if I run rc.local from a terminal window, the rails app starts and stays running.  But when it runs at start up, it exits immediately.  I guess it's getting killed when rc.local exits.  

So now my [hopefully final] question is: how do I kick something off in rc.local that keeps running after rc.local exits?

---

### Post by lkjoel on 2010-06-20
If I get what you men correctly, maybe this could work
```
[sudo] /etc/rc.local &
```
& means it to run in the background

---

### Post by anotherlinuxnewbie on 2010-06-21
Thanks for the reply.

I actually want the command that's IN rc.local to keep running after rc.local exits, and I tried putting the & at the end of my command, but it doesn't work: the shell running the rails server still closes, evidently, when rc.local exits.

---

### Post by lkjoel on 2010-06-21
Ok. Change rc.local to this:
```
#!/bin/sh -e

sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh > /home/jenko/rclocal_executed &

exit 0
```

---

### Post by anotherlinuxnewbie on 2010-06-21
(Thanks for sticking with me, btw.)

Yeah, that's what I tried. Here's my /etc/rc.local:

```
#!/bin/sh -e
sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh  > /home/jenko/rclocal_executed &

exit 0

```

 As you can see, I'm piping out the output of the sh command to /home/jenko/rclocal_executed, which outputs the following:

```
/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
=> Booting Mongrel (use 'script/server webrick' to force WEBrick)
=> Rails 2.2.2 application starting on http://0.0.0.0:3000
=> Call with -d to detach
=> Ctrl-C to shutdown server
Exiting
```


So the rails server is starting up fine, but then it exits, I presume because rc.local is finished.  (I also tried it with the " > /home/jenko/rclocal_executed " removed.) In any case, when I test the app in a browswer, I get this:

```
Oops! Google Chrome could not connect to 192.168.0.46:3000
```

Again, when I run the script from the terminal window everything's fine. ](*,)

---

### Post by lkjoel on 2010-06-21
Ok, replace it with this code
```
#!/bin/sh -e
sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh &

exit 0
```

---

### Post by anotherlinuxnewbie on 2010-06-21
I copied and pasted your code, my rc.local now looks like this: 

```
#!/bin/sh -e
sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh &

exit 
```

Same thing, fails in browser.

---

### Post by lkjoel on 2010-06-21
Ok, what I am gonna suggest is quite risky. It will not exit.
```
#!/bin/sh -e

sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh > /home/jenko/rclocal_executed

```
Then run it as
```
/etc/rc.local &
```

---

### Post by anotherlinuxnewbie on 2010-06-21
if I run the command

/etc/rc.local &

in the terminal window, all is well (i.e., I can bring the site up in the browser).  But that was also true for the older versions, because as long as there's a terminal window to run in, the app keeps running as long as the terminal window is around.  But when I restart the machine, and just depend on that code running automatically at boot, it still fails.

I wouldn't have thought this would be so hard. Thanks again.

---

### Post by lkjoel on 2010-07-02
Sorry for the long wait.

In a terminal window, type:
```
gedit rails.sh
```
in gedit, type:
```
/etc/rc.local &
```
save it and close, and in the terminal window:
```
chmod +x rails.sh
cp rails.sh /boot/rails.sh
```
Tell me if that works out for you!

---

### Post by teisho on 2010-07-02
If you install tihin and add it to rc-defaults you can do this easily.  There's a great article on how to do this at

[http://articles.slicehost.com/2009/2/20/ubuntu-intrepid-thin-web-server-for-ruby](http://articles.slicehost.com/2009/2/20/ubuntu-intrepid-thin-web-server-for-ruby)

Basically once you installed thin, you would add it to defaults like this
```
sudo /usr/sbin/update-rc.d -f thin defaults
```And then configure it to start your rails applicatoin at startup like this
```
sudo thin config -C /etc/thin/tracks.yml -c /home/jenko/public_html/tracks/  --servers 1 -e production
```This is how rails applications are set to run automatically on webservers.

---

### Post by lkjoel on 2010-07-05
> **lkjoel said:**
> Sorry for the long wait.

In a terminal window, type:
```
gedit rails.sh
```in gedit, type:
```
/etc/rc.local &
```save it and close, and in the terminal window:
```
**sudo** chmod +x rails.sh
**sudo** cp rails.sh /boot/rails.sh
```Tell me if that works out for you!
Oops I made another mistake! check the bolded sections.

---

### Post by chensamurai on 2010-12-23
> **anotherlinuxnewbie said:**
> I copied and pasted your code, my rc.local now looks like this: 

```
#!/bin/sh -e
sudo -u jenko PATH=/home/jenko/.rvm/gems/ruby-1.8.7-p174/bin:/home/jenko/.rvm/gems/ruby-1.8.7-p174@global/bin:/home/jenko/.rvm/rubies/ruby-1.8.7-p174/bin:/home/jenko/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games sh /home/jenko/tracks/tracks.sh &

exit 
```

Same thing, fails in browser.

It seems like you could just do this:
[http://ubuntuforums.org/showthread.php?t=646344](http://ubuntuforums.org/showthread.php?t=646344)

Add this to your rc.local:
/usr/local/bin/ruby /home/username/path-to-project/script/server [start-option] -p[####]

---

