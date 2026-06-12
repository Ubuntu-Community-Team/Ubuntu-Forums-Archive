---
title: "pulling jpg png files from numerous folders"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by GMachine_24 on 2010-01-30
Hi. I have a music collection on a hard drive - all under the directory /music1 - and this is hundreds of cds, most with cover art.

I want to pull copies of all the cover art in the numerous directories and sub-directories and put them in a separate folder - I'm trying to do something artistic with the cover art. Yeah, well.

Anyway, it seems, in the back of my mind, that there is a program I can run to scan that hard drive, compile a list of all the jpg files and then pipe copies of them to a separate folder.

Is this possible?

Thanks in advance.

---

### Post by tom.swartz07 on 2010-01-30
> **GMachine_24 said:**
> Hi. I have a music collection on a hard drive - all under the directory /music1 - and this is hundreds of cds, most with cover art.

I want to pull copies of all the cover art in the numerous directories and sub-directories and put them in a separate folder - I'm trying to do something artistic with the cover art. Yeah, well.

Anyway, it seems, in the back of my mind, that there is a program I can run to scan that hard drive, compile a list of all the jpg files and then pipe copies of them to a separate folder.

Is this possible?

Thanks in advance.

The first thing that comes to my head is setting up a terminal command to just locate them and copy them to a folder

DONT USE THIS CODE! im just using it as an example- perhaps you, or someone else could fine tune it for your use


```
locate /music1/*.{jpg,png} | cp /new/folder
```

Something like that would be able to find any file with a jpg or png extension and then copy it to a new folder. You will definitely need to change the setup more specifically for your system, but all you need is a simple command like that!

---

### Post by falconindy on 2010-01-30
I don't believe cp can accept stdin as its source. The find command seems to be your best bet here:
```
find /music1/ -iname *.png -iname *.jpg -exec cp "{}" /new/folder/ \;
```
If you're copying these files to a location on the same physical drive, I would suggest making these hard links instead of true copies, to save space. To do that, simply invoke 'cp' with its '-l' flag.

---

### Post by tom.swartz07 on 2010-01-30
> **falconindy said:**
> I don't believe cp can accept stdin as its source. The find command seems to be your best bet here:
```
find /music1/ -iname *.png -iname *.jpg -exec cp "{}" /new/folder/ \;
```
If you're copying these files to a location on the same physical drive, I would suggest making these hard links instead of true copies, to save space. To do that, simply invoke 'cp' with its '-l' flag.

See! I told you someone would have a way better version of what I was thinking. Thanks falconindy!

That command should copy it to the path that /new/folder points to- you just need to tweak that part. Or as he says, change cp "{}" to cp -l "{}" to create links to the files instead of copying

---

### Post by Mornedhel on 2010-01-30
> **falconindy said:**
> I don't believe cp can accept stdin as its source. The find command seems to be your best bet here:
```
find /music1/ -iname *.png -iname *.jpg -exec cp "{}" /new/folder/ \;
```
If you're copying these files to a location on the same physical drive, I would suggest making these hard links instead of true copies, to save space. To do that, simply invoke 'cp' with its '-l' flag.

find uses -and as the default, doesn't it ? I think you'll need ```
\( -iname '*.png' -or -iname '*.jpg' \)
``` or something approaching.

Also, you may want to replace \; with + to have it call cp only once.

OP: Try it with an added echo, like ```
-exec echo cp [same thing as above]
```

to have it display the command(s) it would perform without the echo.

---

### Post by falconindy on 2010-01-30
You're correct about find defaulting to using 'and' for multiple args. My mistake.

However, find **will** run the args to -exec for each result. It's because of this functionality that you need the escaped semi-colon at the end of the -exec flag. Commands are strung together based on this termination.

---

### Post by Mornedhel on 2010-01-30
> **falconindy said:**
> You're correct about find defaulting to using 'and' for multiple args. My mistake.

However, find **will** run the args to -exec for each result. It's because of this functionality that you need the escaped semi-colon at the end of the -exec flag. Commands are strung together based on this termination.

That's my point, actually: with \; cp will be run for each match (so once by cover art picture: cp foo.jpg target/ then cp bar.png target/ then cp tiger.jpg target/ etc.), whereas with + cp will be run once with all matches (cp foo.jpg bar.png tiger.jpg target/).

---

### Post by falconindy on 2010-01-30
Neat -- that's not a functionality I was aware of. Except I'm not understanding how this enables you to append a source onto the end of the exec because everything is strung together. If that's the case, you might as well just do the following:
```
files=($(find path/ -someflags -exec echo "{}" +))
cp "${files[@]}" target
```
It does slightly irk me to realize that the other solution spawns a buttload of instances of 'cp', but somehow I don't think its going to break anything as its not done in parallel.

---

### Post by Mornedhel on 2010-01-30
> **falconindy said:**
> Neat -- that's not a functionality I was aware of. Except I'm not understanding how this enables you to append a source onto the end of the exec because everything is strung together. If that's the case, you might as well just do the following:
```
files=($(find path/ -someflags -exec echo "{}" +))
cp "${files[@]}" target
```

It does slightly irk me to realize that the other solution spawns a buttload of instances of 'cp', but somehow I don't think its going to break anything as its not done in parallel.

You can just do -exec cp '{}' target/ + and it copies everything to target/ -- of course this works best if there is only one target. Since it spawns cp only once it's equivalent to your solution.

```
find ~/Music -iname *.ogg -exec vorbisgain '{}' +
```

Using \; here would not break anything, as you note, but it gets really interesting to use + because A. vorbisgain takes some time to start up, for some reason, so calling it is expensive, and B. vorbisgain can also do some replay-gain trickery if given more than one filename (album-wide volume normalization, etc.), which you can't with \;.

Note that stringing -test -exec foo '{}' + -or -othertest -exec bar '{}' + will do what you expect, which is call foo once and bar once. I used the above example with other file types (flac) to normalize volume over my entire collection with a find one-liner. You can do it in two passes or more, but you get more street cred with a one liner, of course :)

---

### Post by falconindy on 2010-01-30
Maybe I'm just being dense, but I'm still not getting it. I value my Bash street cred and I'd really like to understand this. Inserting anything between the {} and the trailing + results in find crapping out with a 'missing argument to exec' error. 

I'm messing around with just copying all the files in my home directory to a temporary folder in these examples. nothing exotic.
```
%)&#9472; find . -maxdepth 1 -type f -exec cp '{}' tmp/ +
find: missing argument to `-exec'
```

As I'm a recent ZSH convert, I figured sure... maybe this is an issue with ZSH escaping and globbing. Jump over to my Bash screen...

```
$&#9500;&#9472;> find . -maxdepth 1 -type f -exec cp '{}' tmp/ +
find: missing argument to `-exec'
```

what's up?

---

### Post by Mornedhel on 2010-01-30
OK, I'm kind of blushing in front of my screen here.

What's happening is that POSIX specifies that to use the + terminator, the placeholder {} needs to be the last argument to exec -- that is, immediately before the +.

It just so happens that my examples worked because they satisfy this condition. vorbisgain '{}' +, flac -f --replay-gain '{}' +, rename 's///' '{}' +, etc.

A bug has been reported against findutils to get {} to work anywhere, but it's been closed as WONTFIX -- because the current behavior of findutils respects POSIX and changing it would mean no more POSIX conformance. See [here](http://savannah.gnu.org/bugs/?23439) for the bug report on Savannah.

You can work around this in the case of cp with cp -t /tmp '{}' +, but it's kind of ugly.

---

