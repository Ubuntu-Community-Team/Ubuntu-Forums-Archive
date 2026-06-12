---
title: "Wildcards in proftpd &quot;directory&quot; structure"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2008-03-18
This should be simple according to the proftpd documentation but I can't make it work...

On the server, we have about 30 users. Each has their own directory with an Upload and Download subdirectory. The result we want to achieve is read access only to the Download dir, with write access and OverWrite allowed in the Upload ones.

On an individual level, this works i.e. if I use:

```
<directory /home/public/user1/Upload>
AllowOverwrite on
</directory>
```

This works a treat. However, if I use the following:

```
<directory /home/public/*/Upload>
AllowOverwrite on
</directory>
```

It doesn't, which is a shame as it would make life a lot easier when adding new users. Is there any reason why the wildcards won't work? According to the documentation I should even be able to use two of them (I think):

```
<directory /home/public/*/*/Upload>
```

This would allow us to structure the directories based on department as well as use. Nice, but not necessary if it can be figured out.

Obviously, there are more permissions than just the AllowOverwrite to be configured! They would all be easier if the wildcards worked though!

Hope this is clear :)

---

### Post by superprash2003 on 2008-03-18
consider using gproftpd.. its a GUI for proftpd.. you can install it via synaptic.. it makes it easier for you to configure your ftp setup

---

### Post by IainPurdie on 2008-03-18
That takes half the fun out of it ;)

Will have a look - ta.

Update - OK, I would if I could figure out how to get hold of it... I'm being bounced around two websites and being given some bizarre instructions about adding lines to my sources.list file with no actual guarantee of what I'll be downloading afterwards...

Update2 - no luck. I've tried all the instructions at [www.seerofsouls.com](www.seerofsouls.com) and can't get the package (or any package) to install. Through Synaptics, I just can't find anything if I search, and going via the commandline I get "broken packages" errors :(

Update 3 - managed to download the package elsewhere, but when I run the Autoinstall I'm informed that there isn't a suitable C Compiler in my $PATH. I have checked avd I have /usr/bin/gcc-4.0 installed, and usr/bin is in my $PATH... I am now searching for a nice, traditional, red brick wall to bang my head off.

---

