---
title: "C compile error"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-13
The following code gave me an error:

```

{  
    int IRAYg;  
    FILE *fid;       
    fid = fopen("Input","w");
      (fid == NULL){
      printf("Can not print input file!!!\n");
      exit(0);  
   };

    for(){

      printf("Here is the data");
      fclose(fid);

      };
    }

```

test4.c:132: error: expected ‘;’ before ‘{’ token

I checked my K&R and other sources and the code seems fine. There should be no ; before {. In other words line 132 should not be like this.

(fid == NULL);{. 

Its original form is correct. So how do I get rid of the error?

Newport_j

---

### Post by snova on 2010-04-13
> **newport_j said:**
> The following code gave me an error:

```

{  
    int IRAYg;  
    FILE *fid;       
    fid = fopen("Input","w");
      (fid == NULL){
      printf("Can not print input file!!!\n");
      exit(0);  
   };

    for(){

      printf("Here is the data");
      fclose(fid);

      };
    }

```

test4.c:132: error: expected ‘;’ before ‘{’ token

I checked my K&R and other sources and the code seems fine. There should be no ; before {. In other words line 132 should not be like this.

(fid == NULL);{. 

Its original form is correct. So how do I get rid of the error?

Newport_j

... are you missing an **if**? because **(fid == NULL)** won't do anything useful.

---

### Post by avidday on 2010-04-13
> **newport_j said:**
> The following code gave me an error:

```

    fid = fopen("Input","w");
```


Something tells me that is going to end in tears. Maybe it is a good thing you can't get the code to compile...

---

