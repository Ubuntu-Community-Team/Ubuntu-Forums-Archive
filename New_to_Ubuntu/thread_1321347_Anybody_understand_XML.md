---
title: "Anybody understand XML?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by FreewheelinFrank on 2009-11-10
I'm using Mail-Notification and want to add a custom command to open the Hotmail webmail site when I click on the notification icon. According to the help file, it should be possible to do this:

> To define a custom action for a particular mailbox, edit the ~/.gnome2/mail-notification/mailboxes.xml file and specify a command to be executed when the action button is clicked.

I'd like to run this script when the button is clicked:

```
#!/bin/sh

firefox http://my-hotmail-inbox-address.com
```

The Hotmail entry in the XML file looks like this:

```
<mailbox type="hotmail" name="Hotmail" username="freewheelinfrank@hotmail.com"/>
```

The helpfile says I need to add an XML attribute:

> XML attributes should be added to the mailbox element of the mailbox you want the actions to be available for.

This is the action attribute:

```
Open	open-command
```

This is an example of how to execute a command from the help file:

```
<?xml version="1.0"?>
<mailboxes>
  <mailbox
    type="custom-vfs"
    uri="file:///home/jylefort/Mail/misc"
    open-command="my-open-script %filename"
    mark-as-spam-command="my-spam-script %filename"/>
</mailboxes>
```

I can't see how to apply this to my Hotmail mailbox. I'm sure it must be very obvious to anybody familiar with XML.

Can anybody help?

---

### Post by KIAaze on 2009-11-12
What mail program do you use?

My guess would be:
```
<mailbox
 type="hotmail"
 name="Hotmail"
 username="freewheelinfrank@hotmail.com"
 open-command="~/bin/open_hotmail.sh %filename" />

```
just like in the example.

Name your script "open_hotmail.sh", save it in "~/bin" and make it executable (chmod +x ~/bin/open_hotmail.sh) and hopefully it should work.

Here's what an XML attribute is:
[http://www.w3schools.com/Xml/xml_attributes.asp](http://www.w3schools.com/Xml/xml_attributes.asp)

---

### Post by FreewheelinFrank on 2009-11-12
Wow! thanks! that seems to have done it!

I was trying a lot of things along the same line but obviously I hadn't got the syntax exactly right.

This command now allows me to go straight to the webmail URL for a new Hotmail email without looking for the bookmark (or opening my mail program).

Thanks again!

---

### Post by coldReactive on 2009-11-12
This is why we should be using HTML to do things.

Or better yet, PHP and MySQL.

---

