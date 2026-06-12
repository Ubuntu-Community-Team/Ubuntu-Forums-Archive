---
title: "Trying to make a XML based picture switching background, but..."
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Kevin Flynn on 2011-05-04
Hello, I'm new to this forum...   Ubuntu 10.10 and Gnome 2.32

     I've been trying to find a way to just make a simple 2 frame GIF file my background wallpaper.  I spent 2 days now "Googling" and even searching this forum.  Almost every answer has said "xwinwrap, xwinwrap, xwinwrap!"  Xwinwrap either isn't working or isn't installed right.  Then I find out that in the appearance settings there actually is picture switching wallpapers that use an XML file which can be changed to switch pictures as quickly as one second.  Which is perfect for what I want to do.  Plus this method doesn't involve a second running service.  I took  their own XML file and changed it to fit my needs, but it didn't work.  So, I started by changing it to show just one picture, but I don't know XML at all.  (I know a little HTML and a little javascript) So, it still didn't work.  When I roll the mouse pointer over my wallpaper it says "image missing."  Here is the XML I wrote:

&#65279;<background>
	<starttime>
		<year>
		2011
		</year>
		<month>
		05
		</month>
		<day>
		03
		</day>
		<hour>
		0
		</hour>
		<minute>
		00
		</minute>
		<second>
		01
		</second>
	</starttime>
	<static>
		<duration>100.0</duration>
		<file>/user/TerminalA.jpg/</file>
	</static>
</background>

---

