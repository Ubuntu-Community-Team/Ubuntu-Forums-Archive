---
title: "Syntax Error"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by newport_j on 2009-09-15
What is wrong with file cutil.h. I am using the cuda_instrument.pl script to look for bank conflicts and race conditions in an example file scan.cu.

I get the following output

./cuda_instrument.pl  scan.cu instr.cu
-E- Fatal error parsing input file (see errors below for line numbers in temporary file)

/usr/include/cutil.h[124:0-0] : syntax error
Parsing error
Fatal error: exception Frontc.ParseError("Parse error")



The cutil.h lines in questions are 

//!       deallocate the memory
    ////////////////////////////////////////////////////////////////////////////
    DLL_MAPPING
    CUTBoolean CUTIL_API 
    cutReadFiled( const char* filename, double** data, unsigned int* len, 
                  bool verbose = false);

    ////////////////////////////////////////////////////////////////////////////
    //! Read file \filename containing integer data

bool verbose = false);   is line 124.


I just do not see the error.

newport_j

---

### Post by stderr on 2009-09-15
It's my understanding that you can't intialise variables in header files, because you're simply defining them. The variables don't actually exist yet. So you'll need to set verbose to false in a .c/cpp file.

---

