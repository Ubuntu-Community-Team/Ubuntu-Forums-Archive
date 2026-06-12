---
title: "Filtering HTTP Mime Type"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by nlbs on 2007-10-17
What I want basically is only text/image download from Browser.
for that how can I allow Only those HTTP response that has MIME-type text/* or image/*
and disallow all others. with some firewalls or Iptables. 
Is it possible ??

---

### Post by kidders on 2007-10-18
Hi there,

Firewalls are too low-level for this sort of thing. They operate at the packet level, which is miles away from being able to extract HTTP header information. Personally, I would use a proxy (eg squid) and perhaps a content filter (eg dansguardian).

It's important to realise though that there is a distinction between disallowing certain MIME types (as declared by a web server), and disallowing certain *file* types (as downloaded by a PC inside your LAN). Web servers frequently misidentify data they are serving, so it's commonplace to see executable binaries, compressed archives & other data labelled as "text/plain", for example. In addition, certain XML files tend to be served with the "application/" MIME specifier, so your scheme may turn out to behave inconsistently with certain text files (eg blocking some RSS feeds, but not others). On top of that, should any of your users come to suspect how your content filter works, circumventing it would be trivial, so the scheme you described wouldn't, for example, be useful as a security measure to block access to Windows executables, ZIP archives, and so on ... something many network admins like to do, to limit exposure to viruses.

So, depending on *why* you want to block access to certain content, you may find you'll need something much more sophisticated than a MIME type filter ... but the software I mentioned can still help you.

---

### Post by tonybaqain on 2007-10-19
An Example on squid

First open squid.conf file /etc/squid/squid.conf:
```

# vi /etc/squid/squid.conf

```

Now add following lines to your squid ACL section:
acl blockfiles urlpath_regex “/etc/squid/blocks.files.acl”
You want display custom error message when a file is blocked:

```

# Deny all blocked extension
deny_info ERR_BLOCKED_FILES blockfiles
http_access deny blockfiles

```

Save and close the file.

Create custom error message HTML file called ERR_BLOCKED_FILES in /etc/squid/error/ directory or /usr/share/squid/errors/English directory.

```

# vi ERR_BLOCKED_FILES

```

Append following content:

```

<HTML>
<HEAD>
<TITLE>ERROR: Blocked file content</TITLE>
</HEAD>
<BODY>
<H1>File is blocked due to new IT policy</H1>
<p>Please contact helpdesk for more information:</p>
Phone: 555-12435 (ext 44)<br>
Email: helpdesk@yourcorp.com<br>

```

[INDENT][INDENT][COLOR="Red"]Caution: Do not include HTML close tags </HTML> </BODY> as it will be closed by squid.[/COLOR][/INDENT][/INDENT]
Now create /etc/squid/blocks.files.acl file:

```

# vi /etc/squid/blocks.files.acl

```

Append following text (regular expressions):

```

\.[Ee][Xx][Ee]$
\.[Aa][Vv][Ii]$
\.[Mm][Pp][Gg]$
\.[Mm][Pp][Ee][Gg]$
\.[Mm][Pp]3$

```

for example the **\.[Ee][Xx][Ee]$** can catch multiple forms of .exe extentions, as it is case sensitive; like *---.Exe* or *----.eXe* .... etc

Save and close the file. Restart Squid:

```
# /etc/init.d/squid restart
```

---

### Post by nlbs on 2007-10-20
I'll give it a try

---

