---
title: "Tar Pipeline Trouble"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Windy_Chill on 2011-01-10
Well, I have more trouble with the tar command. I am trying to get the output of one tar command to be used as the input of a second tar command with a pipeline. The first part of the command seems to work. Because, when I enter it I get the file output to my screen. But, when I enter the entire command I get the error below.
```
 james@james-laptop:/old$ sudo tar c * | tar x /new/test.tar
tar: /new/test.tar: Not found in archive
tar: Exiting with failure status due to previous errors 
```

I'm not quite sure what is wrong. Both directories exist on my root file system. Any help with this would be great.

---

