---
title: "Modifying Subject Header in Exim"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by BrnN8r on 2008-11-25
Hi I'm running Ubuntu 8.04 and Exim 4.69 and need some help in modifying the subject header in outgoing emails. 

Basically I want to convert the subject header for an email of the form

Subject: [APPNAME] -- (PROJECT) -- Comment => Subject: Comment

for a specific destination address (i.e. not all emails of this form but only those destined for a specific address)

Does anyone know if this is possible in exim?

Cheers
Steve

---

### Post by BrnN8r on 2008-12-01
In case anyone was interested I figured it out.

I added a system filter to my exim config file.

```
system_filter = /etc/exim4/system_filter
system_filter_user = Debian-exim
system_filter_group = Debian-exim
system_filter_file_transport = address_file
system_filter_pipe_transport = address_pipe
```

and the contents of /etc/exim4/system_filter were roughly:

```
# Exim filter

# Only run this on the first pass through the filter
if not first_delivery then
        finish
endif
  
# Trap any errors
if error_message then
        finish
endif

# Modify the subject header to only include the comments section for all JIRA emails.
if $recipients contains "destination@address.com" and $header_subject: matches \N^\[JIRA\]\s+\w+:\s+.\w+-\d+.\s+.*\N
then
        headers add "parsed-Subject: ${sg{$h_subject:}{^\\\\[JIRA\\\\]\\\\s+\\\\w+:\\\\s+\\\\(\\\\w+-\\\\d+\\\\)\\\\s+}{}}"
        headers remove "Subject"
        headers add "Subject: $h_parsed-Subject"
        headers remove "parsed-Subject"
endif
```

Maybe not optimal but it worked.

---

