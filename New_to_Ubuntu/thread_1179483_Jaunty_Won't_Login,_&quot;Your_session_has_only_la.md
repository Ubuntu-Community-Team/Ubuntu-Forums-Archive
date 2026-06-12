---
title: "Jaunty Won't Login, &quot;Your session has only lasted...&quot;"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by vinay427 on 2009-06-05
Hey,
I got the error "Your session has only lasted less than 10 seconds.  If you..." and when I click on "View details (~/.xsession-errors file)" I get
```
/usr/bin/X11/
/etc/gdm/PreSession/Default: 25: Syntax error: "}" unexpected
gdm[3208]: ERROR: session_child_run: Execution of PreSession script returned > 0. Aborting.
aborting...
```

I'm not sure what I'm supposed to do.  I went to recovery mode (Ctrl+Alt+F2) and typed "gnome-session" and I get "WARNING: Cannot open display."  Please help!

Also, I recently updated a graphics driver unofficially because programs like Boxee and Elisa wouldn't open.  Now they still don't open.  [This]("http://ubuntuforums.org/showthread.php?t=1172552") is my thread for that issue if you have any suggestions.  I tried the suggestions in [this]("http://ubuntuforums.org/showthread.php?t=1058852") thread to fix the login issue but they didn't help.  If you give me a command and tell me to give the output, I can't really do it if it's really long because I can't login to copy/paste.  I'm writing this from another computer.  Also, how to do start a failsafe session?  It says to do that in the "Your session has only lasted..." dialog box.

Thanks in advance! :)

---

### Post by vinay427 on 2009-06-05
Please help!  I really need a solution by today, if that's possible.

---

### Post by ad_267 on 2009-06-05
Can you post the output of:
cat /etc/gdm/PreSession/Default

---

### Post by vinay427 on 2009-06-06
> **ad_267 said:**
> Can you post the output of:
cat /etc/gdm/PreSession/Default

Ok.  I'll try it today (not at the computer now) and post the results.  Thanks!

---

### Post by philinux on 2009-06-06
At the login screen note the Options link. Click that and choose change session. Choose failsafe.

---

### Post by philinux on 2009-06-06
At the login screen note the Options link. Click that and choose select session. Choose failsafe.

---

### Post by vinay427 on 2009-06-06
> **ad_267 said:**
> Can you post the output of:
cat /etc/gdm/PreSession/Default

The output:
```
#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {# Add the missing register to /proc/mtrr
if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
    echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
fi
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then

	CHECKBACKCOLOR="OK"
	if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
		BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

		CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
		if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
			BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
		else
			BACKCOLOR=""
		fi
	fi

	# If we tried to load the themed backgroundcolor, but failed, then try loading plain color
	if [ "x$CHECKBACKCOLOR" != "xOK" ] || [ "x$GDM_GREETER_TYPE" = "xPLAIN" ]; then

		# Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image 
		BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""
			fi
		fi
	fi

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#76848F"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

```

> **philinux said:**
> At the login screen note the Options link. Click that and choose change session. Choose failsafe.

Thanks a lot!  This let me copy/paste the output above easily!  Also, now I have a temporary solution. :D

---

### Post by RedSocrates on 2009-06-06
Have you been hand-editing your /etc/gdm/PreSession/Default?  It looks to me like you've tried to apply a "fix" that I've seen passed around for Intel graphics.  If that's so, it looks like you've applied the fix in the wrong place.  Now, I'm no super-hero of bash scripting, so I don't know if this will fix your issue, but...

Locate the following lines from your /etc/gdm/PreSession/Default:

```
gdmwhich () {# Add the missing register to /proc/mtrr
if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
    echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
fi
```And cut out everything after the '{'.  That is, cut out:

```
# Add the missing register to /proc/mtrr
 if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
     echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
 fi
```so that all that remains is: 

```
gdmwhich () {
```followed by the rest of the file.

You can then re-paste the following into your /etc/gdm/PreSession/Default file, but only AFTER the '}' that stands on a line all by itself; paste the code beginning on a new line: 

```
# Add the missing register to /proc/mtrr
if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
    echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
fi
```Then save the file, restart the computer, and see if you can log in as usual.  Good luck!

---

### Post by RedSocrates on 2009-06-06
Just to clarify my above post, this is what the relevant section of /etc/gdm/PreSession/Default should look like after you've applied the edits:

```
gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# Add the missing register to /proc/mtrr
if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
    echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
fi

```

Having checked my own /etc/gdm/PreSession/Default, I'm now somewhat more confident that this is the cause of your problems.

---

### Post by vinay427 on 2009-06-06
Now that I think of it, that must be the problem.  I found an Intel graphics fix but didn't know how to apply it so I sort of guessed.  Woops...  I'll try that today.  Thanks a lot!

> **RedSocrates said:**
> Just to clarify my above post, this is what the relevant section of /etc/gdm/PreSession/Default should look like after you've applied the edits:

```
gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# Add the missing register to /proc/mtrr
if test ! "x$(cat /proc/mtrr | grep write-combining)" = "" ; then
    echo "base=0x0200000 size=0x1000000 type=write-combining" > /proc/mtrr
fi

```

Having checked my own /etc/gdm/PreSession/Default, I'm now somewhat more confident that this is the cause of your problems.

---

### Post by vinay427 on 2009-06-06
Thanks a lot!  It worked great.  If you have any suggestions for [this]("http://http://ubuntuforums.org/showthread.php?t=1172552") thread it would be great because I formatted my whole computer and installed Ubuntu just to have a great media center experience but now I can't.  Thanks a lot (for this and in advance for that)!

---

### Post by rpkopreski on 2009-07-03
Hi, I am having a similar problem.  It started after I allowed a system update.  I get the same "Your session has only lasted..." message but the detailed view shows the following summarized:

error: /etc/gdm/xsession: libc.so.6: cannot open shared object file. no such file or directory
error: /etc/gdm/xsession: librt.so.1: cannot open shared object file. no such file or directory
error: /usr/bin/perl: libdl.so.2: cannot open shared object file. no such file or directory

Any idea what's happening?

I can only login with GNOME failsafe option.

Thanks in Advance

---

