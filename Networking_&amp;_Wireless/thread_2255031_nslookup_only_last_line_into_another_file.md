---
title: "nslookup only last line into another file"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2014-12-01
I want to know how to only have the last line of the nslookup command showing the ip address. then take that address and put it into the second line of another document in the first column. can this be done?

---

### Post by gordintoronto on 2014-12-02
String nslookup with grep to get the first part. Can you make two documents, one with the first line, and another with the third to last lines, then string them all together?

What is the exact nslookup command you are using?

---

### Post by slickymaster on 2014-12-02
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by SeijiSensei on 2014-12-02
Usually the "host" command is easier to work with, for instance:
```

$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12

$ host -t ns ubuntuforums.org
ubuntuforums.org name server ns3.canonical.com.
ubuntuforums.org name server ns1.canonical.com.
ubuntuforums.org name server ns2.canonical.com.

```
For instance, to get the IP address for a name, I'd use:
```
host host.example.com | awk '{print $4}'
```

---

