---
title: "Help burning files to a specified sector"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Jeremywilms on 2009-09-27
I've been writing a bootsector, I have successfully tested and run it when using software such as MagicIso to create a bootable image, I can't get it to start the kernel though, the reason being I do not know how to burn a file to a certain sector of an image. As my bootsector assumes the kernel is located on the second sector of the drive it was booted on. So how can I, for example, place a binary file on the second sector(and having it span over several sectors if needed)?

Also, I shouldn't have said 'burn', because what I really mean is to have it written to an ISO\IMG file.

I am aware of the dd shell command, it might be what I'm looking for, but I've tried several times and I can't get it to work.

It's 2:21AM, and that's my excuse for the poor wording :)

Thanks.
[B]
*Edit*[/B]
Noticed this isn't the correct place for this question, feel free to move it.

---

### Post by Jeremywilms on 2009-09-27
Can someone move this thread to a more suitable location. Thanks.

---

### Post by bodhi.zazen on 2009-09-27
You can use the dd command to do this. 

[http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/](http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/)

Basically that over writes the MBR.

Other then installing some kind of boot program or application I have no idea what you are asking or what your problem may be.

---

### Post by Jeremywilms on 2009-09-27
Thank you for your help.

After researching a bit on the .img format, it turns out it's pretty simple to write your own application to write sectors for you, which I did last night, and assumed it hadn't worked but just required a small bug to be fixed. Thanks for your help, greatly appreciated.

For those who land on this page for the same reason I did:
(Note no practice is enforced, neither was commenting, this was just supposed to be a small quick tool, nothing more, and I'm sure it has a couple of bugs.)

main.h
```

/**
 *  Written by Jeremy. A. Wildsmith
 */

typedef struct FileData 
{
	char  sInputFile[50];
	int   iReqSector;

	int   iSize;
	
	int   iValid;	

	FILE* file;

} FILEDATA, *PFILEDATA;


int print_usage(char* source);

int GenerateFileData(int args, char** argv, PFILEDATA fileDataOut);
int PrintFileDataCollection(int numberOfElements, PFILEDATA fileDataCollection);

int InitFileForCollection(int numElements, PFILEDATA fileDataCollection)

int WriteImageFile(int numberOfSectors, int numberOfElements, PFILEDATA fileDataCollection, FILE* outputFile);
int WriteImageSectors(char* data, int dataLength, FILE* outputFile);

```
main.c
```

/**
 *  Written by Jeremy. A. Wildsmith
 */


#include <stdio.h>
#include <string.h>
#include <sys/stat.h>


#include "main.h"


int main(int argc, char** argv)
{
	int numOfFiles = 0;
	
	printf("Written by Jeremy. A. Wildsmith\nCopyright imgMaker, 2009, Jeremy. A. Wildsmith\n");

	if(argc < 5)
		return print_usage(argv[0]);

	
	
	FILE* outputFile = fopen(argv[1], "w+");
	if(!outputFile)
	{
		printf("Error opening output file %s\n",argv[1]);
		return 0;
	}

	int totalSectors = atoi(argv[2]);

	FILEDATA fileData[15];
	
	numOfFiles = GenerateFileData(argc - 3, &argv[3], fileData);

	InitFileForCollection(numOfFiles, fileData);
	
	printf("\n\n\t--[File Sector Write List]--\n\n");

	PrintFileDataCollection(numOfFiles, fileData);

	printf("\n\n\t----------------------------\n\n");

	printf("If input files you've selected are not on the list, they've been invalidated\n"
	       "because they could not be accessed.\n\n");

	printf("Total number of sectors in image(%d)\n\t(Must excceed or be equal to the amount being used!)\n\n", totalSectors);

	printf("Data will be written to output exactly as displayed\n"
	       "continue? (y=yes\\n=exit)\n");
	
	char buffer[10];
	scanf("%s", buffer);
	if(strncmp(buffer, "n", 1) == 0)
		return 0;
	
	printf("Now writing img file.\n");
	
	WriteImageFile(totalSectors, numOfFiles, fileData, outputFile);
	return 0;
}

int print_usage(char* source)
{
	printf("[USAGE]\n\t%s output(.img\\.iso) Total_Number_Of_Sectors dataFileOne.bin baseSector etc..\n", source);
	return 1;
}

int GenerateFileData(int args, char** argv, PFILEDATA fileDataOut)
{
	int i 	      = 0;
	int baseParam = 0;

	if(args <= 0)
		return 0;

	for(i = 0; i < args / 2; i++)
	{
		baseParam = i * 2;
		strncpy(fileDataOut[i].sInputFile, argv[baseParam], sizeof(fileDataOut[i].sInputFile));
		fileDataOut[i].iReqSector = atoi(argv[baseParam + 1]);
	}

	return i;
}

int InitFileForCollection(int numElements, PFILEDATA fileDataCollection)
{
	struct stat statBuffer;

	int i = 0;	
	
	for(i = 0; i < numElements; i++)
	{
		fileDataCollection[i].iValid = 0;
		if(!fileDataCollection[i].sInputFile)
			continue;
		
		FILE* fileBuffer = fopen(fileDataCollection[i].sInputFile, "r");
		
		if(!fileBuffer)
			continue;
	
		fileDataCollection[i].file = fileBuffer;

		int status = stat(fileDataCollection[i].sInputFile, &statBuffer);
	
		if(status < 0)
			continue;
		
		fileDataCollection[i].iSize = statBuffer.st_size;
		fileDataCollection[i].iValid = 1;
	}
}

int PrintFileDataCollection(int numberOfElements, PFILEDATA fileDataCollection)
{
	int i = 0;
	for(i = 0; i < numberOfElements; i++)
	{
		if(!fileDataCollection[i].iValid)
			continue;

		printf("[File %d]\n", i);
		printf("\tSource: \t\t%s\n", fileDataCollection[i].sInputFile);
		printf("\tUsing Sectors: \t%d-%d\n", fileDataCollection[i].iReqSector, fileDataCollection[i].iReqSector + GetNumberOfUsedSectors(fileDataCollection[i].iSize));
		printf("\tSize:\t\t\t%d\n", fileDataCollection[i].iSize);
	}
	return 1;
}

int WriteImageFile(int numberOfSectors, int numberOfElements, PFILEDATA fileDataCollection, FILE* outputFile)
{	
	int i = 0;
	
	char nullByte = 0;

	for(i = 0; i < numberOfSectors * 512; i++)
		fwrite(&nullByte, 1, 1, outputFile);	

	printf("Filling output with null sectors\n");

	for(i = 0; i < numberOfElements; i++)
	{
		printf("[File %d]\n", i);
		if(!fileDataCollection[i].iValid)
		{
			printf("\tIgnoring file %d, reason: invalidated.\n", i);
			continue;
		}
		
		printf("\tLoading file contents into buffer.\n");
		char* dataBuffer = (char*) malloc(fileDataCollection[i].iSize);

		fread(dataBuffer, 1, fileDataCollection[i].iSize, fileDataCollection[i].file);

		printf("\tClosing file.\n");
		fclose(fileDataCollection[i].file);

		printf("\tWriting file %d to base sector %d\n", i, fileDataCollection[i].iReqSector);
		printf("\tSetting cursor position to %d\n", fileDataCollection[i].iReqSector * 512);
		int status = fseek(outputFile, fileDataCollection[i].iReqSector * 512, SEEK_SET);
		
		if(status != 0)
		{
			printf("\tError setting cursor position.\n"
			       "\tAborting write of current section\n");		
			continue;
		}
	
		int numWrittenSectors = WriteImageSectors(dataBuffer, fileDataCollection[i].iSize, outputFile);
		
		printf("\tWrote %d sector(s)\n", numWrittenSectors);		
		
	}
	return 1;
}

int WriteImageSectors(char* data, int dataLength, FILE* outputFile)
{
	int sectors        = GetNumberOfUsedSectors(dataLength);
	int nullPaddingLen = (sectors * 512) - dataLength; 
	
	char nullData = 0;
	int  i        = 0;

	fwrite(data, 1, dataLength, outputFile);
	
	for(i = nullPaddingLen; i > 0; i--)
		fwrite(&nullData, 1, 1, outputFile);

	return sectors;
}

int GetNumberOfUsedSectors(int dataLen)
{

	if(dataLen <= 0)
		return 0;

	int numOfSectors = dataLen / 512;
	if(dataLen - (numOfSectors * 512) > 0)
		numOfSectors++;

	return numOfSectors;

}


```

---

