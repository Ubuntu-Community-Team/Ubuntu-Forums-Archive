---
title: "Firefox super slow page loading"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by AgentXSmith on 2009-03-02
Installed some firefox packages a few days ago (procrastinating) and now it takes forever to load up a page.  Checked the error console and it is just brimming over, dozens and dozens of repetitive errors every time I try to load a new page.  I believe that's what slowing it down.  Any fix for this other than going to Opera or something?

Here's a few examples of the errors:

Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 501

Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 506

Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 1023


And just on and on...

---

### Post by x33a on 2009-03-02
try loading a new profile. 

```
firefox -ProfileManager
```

don't add any addons, plugins to the new profile and see if the problem persists.

---

