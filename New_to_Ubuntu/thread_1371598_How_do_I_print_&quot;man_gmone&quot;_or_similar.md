---
title: "How do I print &quot;man gmone&quot; or similar ?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Sailing Bud on 2010-01-03
Using Ubuntu 9.10 with Gnome-Terminal 2.28.1
I am attempting to write a script (maybe 6 months before I should) and am trying to learning how to control terminal windows.  In the process I have been doing a lot of reading.  Now to my questions.

1.) As an example is there a way to print to the printer, not the screen, the output of "man screen" ?
2.) Is there a separate user form for Gnome or Gnome - Terminal ?
3.) What are the best (I know this is subjective) books about ".bash" and "Gnome-Terminal" ?
4.) Is there a "PDF" file of any or all of the info that I am looking for ?

Thanks ahead of time,  I doubt that there will be an answer to all of my questions, I am just looking to get pointed in the correct direction.

Sailing Bud

---

### Post by VCoolio on 2010-01-03
Start here: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
Pdf here: [http://www.tldp.org/LDP/abs/abs-guide.pdf](http://www.tldp.org/LDP/abs/abs-guide.pdf)

---

### Post by JohnnyVW on 2010-01-03
I usually do something like this:

```

man sensors > sensors.txt

```

or

```

man sensors | lpr

```

I'm sure there's a way to pipe the output to a pdf printer.  I'm just having a brain-fart right now on how to do it...

attached is what the first command looks like.

---

### Post by falconindy on 2010-01-03
If you want more than just plain text...

I use this alias to convert man pages to pdf's:
```
man2pdf() {
    if [[ -z $1 ]]; then
    	echo "USAGE: man2pdf [manpage]"
    else
    	if [[ `find /usr/share/man -name $1\* | wc -l` -gt 0 ]]; then
		out=/tmp/$1.pdf
		if [[ ! -e $out ]]; then
			man -t $1 | ps2pdf - > $out
		fi
		if [[ -e $out ]]; then
			/usr/bin/evince $out
		fi
	else
		echo "ERROR: manpage \"$1\" not found."
	fi
    fi
}
```
You can also open a man page as HTML in a browser with the '-H<browser>' option, e.g.:
```
man -Hchromium-browser udev
```

---

### Post by kaibob on 2010-01-04
> **Sailing Bud said:**
> Now to my questions.

1.) As an example is there a way to print to the printer, not the screen, the output of "man screen" ?


The following command--which is adapted from the man page for man--prints the man page for screen to the named printer. 

```
man -t screen | lpr -P Deskjet-6980-series
```

Just to check, I tested this command but using the PDF printer. The resulting document is 47 pages long. The command issued a strange error message, but the document was created without issue.

---

### Post by Sailing Bud on 2010-01-08
Thank you all for the support ! ! !
Sailing Bud

---

### Post by sdrisk8262 on 2010-01-14
I like the idea of printing the man pages out in to a PDF.  But I am not sure how to use what [falconindy]("http://ubuntuforums.org/member.php?u=863375") posted? Is their a version for Dummies?  ex: I need to print a copy or be able to read the "man pppd" manual.

---

