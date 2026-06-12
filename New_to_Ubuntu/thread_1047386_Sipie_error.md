---
title: "Sipie error"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Bluefire on 2009-01-22
Hey Guys,

I just installed Sipie this morning on 8.10, and I'm getting this error when I try to run it.  Any ideas?

gtkSipie
Traceback (most recent call last):
  File "/usr/bin/gtkSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'gui_scripts', 'gtkSipie')()
  File "build/bdist.linux-i686/egg/Sipie/gtkPlayer.py", line 88, in gtkPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 374, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 298, in tryGetStreams
  File "/var/lib/python-support/python2.5/BeautifulSoup.py", line 1499, in __init__
    'th' : ['tr'],
  File "/var/lib/python-support/python2.5/BeautifulSoup.py", line 1230, in __init__
    """We need to pop up to the previous tag of this type, unless
  File "/var/lib/python-support/python2.5/BeautifulSoup.py", line 1263, in _feed
    #If we encounter one of the nesting reset triggers
  File "/usr/lib/python2.5/HTMLParser.py", line 108, in feed
    self.goahead(0)
  File "/usr/lib/python2.5/HTMLParser.py", line 148, in goahead
    k = self.parse_starttag(i)
  File "/usr/lib/python2.5/HTMLParser.py", line 263, in parse_starttag
    % (rawdata[k:endpos][:20],))
  File "/usr/lib/python2.5/HTMLParser.py", line 115, in error
    raise HTMLParseError(message, self.getpos())
HTMLParser.HTMLParseError: junk characters in start tag: u'{height:21px;} value', at line 145, column 26

---

### Post by mjheagle8 on 2009-01-22
the error is in the HTMLParser.py file @ line 115. did you take a look at that file?

---

### Post by Bluefire on 2009-01-22
Yeah, all that line is is this (which isn't helpful):

raise HTMLParseError(message, self.getpos())

---

### Post by OsuSurfRat on 2009-01-22
Wow this is my first post in my first forum.  Exciting.  
I registered today because I am having a the exact same issue. I did find some where that the @ symbol in not defined in the HTML parser.

not sure what that means exactly but I will be glad to share as I find more.  Have you come any closer to a resolution???????

---

### Post by NICU on 2009-01-24
Hi I'm having the same problem.  Unfortunately I'm not a python programmer so I'm not much help.  Let me know if there's anything I can test.

---

### Post by OsuSurfRat on 2009-01-26
I have found a way to listen to sirius!  It seems odd but if you remove your plugins with:

sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player

then update them to:
 
sudo apt-get install mplayer mozilla-mplayer

then I went to the Sirius's radio launcher as I would with Internet Explorer on Windows.

A 'missing plugin' error pops up.  If you just ignore that and wait about 15 - 20 seconds it starts to work.  Igues that you don't need sipie at all.
I still could not get sipie working.

good luck

---

### Post by NICU on 2009-01-26
I have gotten the web player to work before in my browser, but I'd much rather use Sipie if I can get it working. I have it working on another PC which I setup before the Sirius/XM merger so hopefully I can copy over everything from the working PC to my not working PC. 

If anyone else finds something please let us know. As it is, new installations of Sipie won't work, but old ones seem to still work.

---

### Post by OsuSurfRat on 2009-01-27
I used to use Python so I am curious as to the why and how about the whole thing.  I must say though, it is nice to have my talk radio while searching now. 

I did notice that the Python version installed in Unbuntu is 2.5.  I did notice in the set up notes that is claims to work best with 2.6 or greater.

I tried to update/install the later version and ended up disabling and removing most of Ubuntu's software.  To know python is to know the inner workings of most Linux I think.

I think that I will search the python 2.6 update notes to see if I see any changes in the HTML parser modules.  

May I ask what your reason for wanting sipie is?  Is it so you don't have to open a browser?

Good luck and please keep me posted.

---

### Post by NICU on 2009-01-27
I use Sipie on an old PC that's just hooked up to my speakers (no monitor). I have it configured to start up at noon each day to listen to the shows I like. Using the web interface you have to click the window every half hour or hour before it shuts off on me. So using Sipie is definitely a must for me. I'd just like to replace the PC its currently on with a newer one, but new Sipie installs don't work for some reason.  I'll look into python v2.6 after work.

---

### Post by llamakc on 2009-01-31
Bump. Same issue here on 8.10.

---

### Post by crshman on 2009-02-19
I have the same issue, anyone find a fix yet?

---

### Post by TallMatthew on 2009-02-23
I agonized over this for a couple of days.  It turns out this error is a result of the latest version of BeautifulSoup, one of the Python modules that Sipie is based on.  Version 3.1.x will generate the error we're seeing.  Version 3.0.7 works properly.  3.1.x has been the official release since January 6, which explains why sipie isn't currently working for a lot of people.

First you have to uninstall the latest version of BeautifulSoup.  I found a script easy_uninstall.py on the net which will do that for you.  It's attached to this message.

Then the following:

sudo python uninstall.py BeautifulSoup
wget [http://www.crummy.com/software/BeautifulSoup/download/3.x/BeautifulSoup-3.0.7.tar.gz](http://www.crummy.com/software/BeautifulSoup/download/3.x/BeautifulSoup-3.0.7.tar.gz)
tar zxvf BeautifulSoup-3.0.7.tar.gz 
cd BeautifulSoup-3.0.7
sudo python setup.py install

And you should be good!

---

### Post by llamabr on 2009-02-23
Ah, to finally have my sipie back.  Thank you for doing what no man before you could do.

Now to enjoy the last few weeks of my sirius subscription, before I cancel because I don't want to be charged 2 extra bucks for online listening.

Thanks again.

---

### Post by llamakc on 2009-02-23
Great instructions. This worked perfectly. Thanks!

---

### Post by nixIT on 2009-03-17
Hmmm, yesterday Sipie worked perfectly, no updates on my system at all, and now today when I try to launch sipie, I get this:

```

~$ cliSipie
Traceback (most recent call last):
  File "/usr/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 374, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 279, in tryGetStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 157, in __getURL
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 387, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 498, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.5/urllib2.py", line 425, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 506, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 500: Internal Server Error

```

Any ideas?  I am running beautifulsoup 3.07

---

### Post by nixIT on 2009-03-17
Sipie is now working, must have been a website issue.

---

### Post by nixIT on 2009-03-18
> **nixIT said:**
> Hmmm, yesterday Sipie worked perfectly, no updates on my system at all, and now today when I try to launch sipie, I get this:

```

~$ cliSipie
Traceback (most recent call last):
  File "/usr/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 374, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 279, in tryGetStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 157, in __getURL
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 387, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 498, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.5/urllib2.py", line 425, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 506, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 500: Internal Server Error

```

Any ideas?  I am running beautifulsoup 3.07

Hmm, I'm getting the same exact error this AM.  Does anyone know if this is related to sipie?  the sirius servers?

---

### Post by GMeola on 2009-04-06
Great Fix TallMatthew!!!

This fix also worked on Januty 9.04 Beta.

~Gary Meola

---

### Post by Dr. Feltersnatch on 2009-05-08
Tall Matthews fix worked here in 9.04

---

### Post by nixIT on 2009-06-01
Hello all,

Sipie is working, with the exception that today my track lineups are fubar.  I normally listen to Hairnation, sirius 23, and I confirmed their channel lineup from their website.

However, when I used Sipie, I type in:

cliSipie

from a terminal, type in my station (hairnation), and usually I get a nice streaming helping of your favorite hair.  However, today it seems to be streaming alternative music, from Hardattack which I think is now called Liquid Metal.  :(

Has anyone else noticed the channels being not where they should be?  Anyone know how I can get my hair nation back to streaming?

--nixIT

---

### Post by llamabr on 2009-06-08
I can't confirm this, since I shut down my sirius when they wanted to charge 3 extra bucks to listen online.

but cliSipie has tab completion.  type half the name, and tab the rest, to make sure you get the right channel.

---

### Post by nixIT on 2009-06-08
> **TallMatthew said:**
> I agonized over this for a couple of days.  It turns out this error is a result of the latest version of BeautifulSoup, one of the Python modules that Sipie is based on.  Version 3.1.x will generate the error we're seeing.  Version 3.0.7 works properly.  3.1.x has been the official release since January 6, which explains why sipie isn't currently working for a lot of people.

First you have to uninstall the latest version of BeautifulSoup.  I found a script easy_uninstall.py on the net which will do that for you.  It's attached to this message.

Then the following:

sudo python uninstall.py BeautifulSoup
wget [http://www.crummy.com/software/BeautifulSoup/download/3.x/BeautifulSoup-3.0.7.tar.gz](http://www.crummy.com/software/BeautifulSoup/download/3.x/BeautifulSoup-3.0.7.tar.gz)
tar zxvf BeautifulSoup-3.0.7.tar.gz 
cd BeautifulSoup-3.0.7
sudo python setup.py install

And you should be good!

I did this, and I am getting the following error:
```

$ cliSipie
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Traceback (most recent call last):
  File "/usr/local/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 374, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 298, in tryGetStreams
  File "/var/lib/python-support/python2.6/BeautifulSoup.py", line 1499, in __init__
    BeautifulStoneSoup.__init__(self, *args, **kwargs)
  File "/var/lib/python-support/python2.6/BeautifulSoup.py", line 1230, in __init__
    self._feed(isHTML=isHTML)
  File "/var/lib/python-support/python2.6/BeautifulSoup.py", line 1263, in _feed
    self.builder.feed(markup)
  File "/usr/lib/python2.6/HTMLParser.py", line 108, in feed
    self.goahead(0)
  File "/usr/lib/python2.6/HTMLParser.py", line 148, in goahead
    k = self.parse_starttag(i)
  File "/usr/lib/python2.6/HTMLParser.py", line 263, in parse_starttag
    % (rawdata[k:endpos][:20],))
  File "/usr/lib/python2.6/HTMLParser.py", line 115, in error
    raise HTMLParseError(message, self.getpos())
HTMLParser.HTMLParseError: junk characters in start tag: u'{height:21px;} value', at line 145, column 26

```

any idea how to get this fixed.

--nixIT

---

### Post by nixIT on 2009-06-09
Anyone?

I installed Xubuntu on a laptop I acquired, and would love it if I can get sipie to work on it, but as you can see by the above post, I'm receiving the beautiful soup error, even though I installed the earlier version of beautiful soup.

any ideas?

--nixIT

---

### Post by squid68 on 2009-07-10
There is an add-on from Firefox, Sirius Player 1.3.3 that works better than the website and does not have the are you listening every 90 minutes deal. You have to sign in but it works well and will adjust if you have the premium sound subscription. I am using it with Heron. I am not sure if it works out of the box but I have helper plugins like mplayer, realplayer, vlc, quicktime, gxine, etc. installed and mine works fine. I would love to get Sipie back and running but since it died under Gusty I have not tried to re-install it under Heron. The Firefox player should work for those in need while the sipie errors get solved.

---

### Post by nixIT on 2009-09-09
> **squid68 said:**
> There is an add-on from Firefox, Sirius Player 1.3.3 that works better than the website and does not have the are you listening every 90 minutes deal. You have to sign in but it works well and will adjust if you have the premium sound subscription. I am using it with Heron. I am not sure if it works out of the box but I have helper plugins like mplayer, realplayer, vlc, quicktime, gxine, etc. installed and mine works fine. I would love to get Sipie back and running but since it died under Gusty I have not tried to re-install it under Heron. The Firefox player should work for those in need while the sipie errors get solved.

I am still using sipie (cliSipie actually) and it works great, with the exception of the following:

```

~$ cliSipie
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Enter stream: hairnation
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/StreamHandler.py:62: DeprecationWarning: os.popen4 is deprecated.  Use the subprocess module.

```

Any idea why I get this?  Are there any fixes for it?  Like I said, cliSipie works fine, though I am worried that it may end up quit working with one of the future versions of Ubuntu.

--nixIT.

---

