---
title: "proper file syntax"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by squrl on 2010-10-29
timidity ~/Desktop/conversionfolder/*.mid -O -o ~/Desktop/conversionfolder/*.wav

The above line works. The problem is it outputs to a single file named *.wav What do I use in place of * to get the same output file name as the input?

Thanks

---

### Post by sisco311 on 2010-10-29
Try something like:
```

for file in ~/Desktop/conversionfolder/*.mid; do timidity "${file}" -O -o "${file//.mid/.wav}"; done

```

---

### Post by squrl on 2010-10-29
It worked perfectly  Thanks

---

