---
title: "wireless-info script error 16.04"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by moot2 on 2016-05-21
This a new install of Ubuntu 16.04.
I ran the wireless-info script using:
     ```


     wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \ chmod +x wireless-info && \ ./wireless-info

```

The terminal screen output:
TY194-Ubuntu-16-04:~/Desktop$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wire.../wireless-info]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info") && \ chmod +x wireless-info && \ ./wireless-info
--2016-05-20 16:25:30--  [https://github.com/UbuntuForums/wire.../wireless-info]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info")
Resolving github.com (github.com)... 192.30.252.131
Connecting to github.com (github.com)|192.30.252.131|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/Ub.../wireless-info]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info") [following]
--2016-05-20 16:25:31--  [https://raw.githubusercontent.com/Ub.../wireless-info]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info")
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.39.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.39.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info              100%[=====================================>]  15.50K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2016-05-20 16:25:31 (1004 KB/s) - &#8216;wireless-info&#8217; saved [15868/15868]

No command ' chmod' found, did you mean:
 Command 'chmod' from package 'coreutils' (main)
 chmod: command not found

The script did not output the wireless-info.txt file (14.04.4 did)

What am I missing?

OK... found space between \ chmod -x... and \ ./wireless-info... in command line... I cut and pasted but must have gotten space from line breaks when I copied from CODE box...
Anyway, removed space... \chmod -x... and \./wireless-info... seems to work now... on to trying to see why wireless won't connect...


-----------------------------------------------------------------------------------------
You can lead a horse to water... but you can't make 'em think

---

### Post by steeldriver on 2016-05-21
Remove the extra backslashes (I don't know how they got in there?)

```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info [COLOR=#0000ff]&& chmod +x wireless-info && ./wireless-info[/COLOR]

```

Or (since you've already done the wget) just

```

chmod +x wireless-info && ./wireless-info

```

---

### Post by moot2 on 2016-05-21
Ok... Thanks...

---

