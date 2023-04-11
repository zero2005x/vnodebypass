vnodebypass
=====================

### An expermental tool to hide jailbreak files for bypass detection.

1.
This is only for iOS 15.7.3 / iPhone 6s now.
It would not work on iOS 15.6 RC(19G69) / iPhone X.
Other iDevice is not test! Please do this on your risk.

2.
I just follow the xsf1re's tip on Twitter to build this project.

2-1
To set kCFCoreFoundationVersionNumber_iOS_15_0 "1854"

2-2
To add following code in get_vnode_with_file_index of kernel.m .

if (kCFCoreFoundationVersionNumber >= kCFCoreFoundationVersionNumber_iOS_15_0)  
		openedfile = kernel_read64(filedesc + (8 * file_index));
	else if(kCFCoreFoundationVersionNumber == kCFCoreFoundationVersionNumber_iOS_15_7_3 || kCFCoreFoundationVersionNumber == kCFCoreFoundationVersionNumber_iOS_15_1)
		openedfile = kernel_read64(fileproc + (8 * file_index));
	else
		printf("not the case I mentioned!\n");
