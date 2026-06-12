---
title: "Dnuos help"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-12-31
Is anyone here familiar with the app Dnuos?

[http://bitheap.org/dnuos/](http://bitheap.org/dnuos/)

I'm wanting to make a database of my music library, which is on my external hard drive. So, I got the app installed. But when I type "dnuos" into Terminal to run it, I get this error:

*No folders to process.*

So, the dnuos page says the app installs a script into /usr/local/bin. So I"m guessing I have to edit that script with my music folder directory? Then everything should work fine? The thing is, I'm still pretty bad at working on Terminal, so I'm not the best at folder structure. It looks to me that my Music folder on my external is located on:

media/disk/Music

But when I edit the script with that directory, nothing happens. Actually I'm not even totally sure what part of the script I"m supposed to edit. The script looks like this:

[I]#!/usr/bin/python
import sys
import dnuos
sys.exit(dnuos.main())[/I]

So if anyone can give me any help on this would be really appreciated.

Thanks.

---

### Post by Temposs on 2009-12-31
You should not be editing the script. Try typing:

```
dnuos --help
```

and post what is shown.

---

### Post by h8uthemost on 2009-12-31
Thanks for the reply Temposs. And the script is back to its original state.

I typed your command and got this:

[PHP]Usage: dnuos [options] basedir ...

Options:
  -h, --help            Show this help message and exit
  --help-output-string  Show output string help message

  Application:
    --debug             Output debug trace to stderr
    --ignore-bad        Don't list files that cause Audiotype failure
    -q, --quiet         Omit progress indication
    -V, --version       Display version

  Caching:
    --cache-dir=DIR     Store cache in DIR (default /home/scott/.dnuos)
    --cull-cache        Cull non-existent cached directories and exit
    --delete-cache      Delete the cache directory and exit
    --disable-cache     Disable caching

  Directory walking:
    -e DIR, --exclude=DIR
                        Exclude DIR from search
    -i, --ignore-case   Case-insensitive directory sorting
    -L, --list-files    List audio files in directories (doesn't use caching)
    -m, --merge         Parse basedirs in parallel and merge output
    -u TYPES, --unknown-types=TYPES
                        A comma-separated list of unknown audio types to list
    -w, --wildcards     Expand wildcards in basedirs

  Filtering:
    -b MIN, --bitrate=MIN
                        Exclude MP3s with bitrate lower than MIN (in Kbps)
    -l, --lame-only     Exclude MP3s with no LAME profile
    -v, --vbr-only      Exclude MP3s with constant bitrates
    -M, --no-mixed      Exclude directories with mixed files

  Output:
    -B COLOR, --bg=COLOR
                        Set HTML background COLOR (default white)
    -f FILE, --file=FILE
                        Write output to FILE
    -H, --html          HTML output (deprecated, use --template html)
    -I n, --indent=n    Set indent to n (default 4)
    -o STRING, --output=STRING
                        Set output format STRING used in plain-text and HTML
                        output. See --help-output-string for details on
                        syntax. (default [n,-52]| [s,5] | [t,-4] | [q])
    -O FILE, --output-db=FILE
                        Write list in output.db format to FILE (deprecated,
                        use --template db)
    -P n, --prefer-tag=n
                        If both ID3v1 and ID3v2 tags exist, prefer n (1 or 2)
                        (default 2)
    -s, --strip         Strip output of field headers and empty directories
    --template=TEMPLATE
                        Set output TEMPLATE (default plaintext)
    -T COLOR, --text=COLOR
                        Set HTML text COLOR (default black)

  Statistics:
    -D, --date          Display datestamp header
    -S, --stats         Display statistics results
    -t, --time          Display elapsed time footer[/PHP]

---

### Post by Temposs on 2009-12-31
right, so this shows you how to use the dnuos program. At the most basic, you just run it like this:

```
dnuos /media/disk/Music
```

If you need any of the other special functionality dnuos offers, then you can see all the different options it gives you when you look at the help.

---

### Post by h8uthemost on 2009-12-31
Unforunately, I'm still getting the No Folders to Process error. I must have the folder structure wrong. Is there some easy way to find out exactly what the folder structure is to my Music folder on my external?

Here's a screenshot of the folder I'm trying to get to. I don't know if this will be of any help or not:

[IMG]http://lookpic.com/i/719/MRzlDe00.png[/IMG]

---

### Post by Temposs on 2009-12-31
Show me the terminal with the command you typed and the output of it.

---

### Post by h8uthemost on 2009-12-31
I got it Temposs. I wasn't cd'ing to /media/disk/Music first. When I was typing this command the directory was still on my Desktop.

Thank you so much for your help. I've been trying to get this to work for days.

---

### Post by Temposs on 2009-12-31
good job :-)

---

