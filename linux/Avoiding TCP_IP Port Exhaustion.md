url: http://msdn.microsoft.com/en-us/library/aa560610%28v=bts.20%29.aspx

When a client initiates a TCP/IP socket connection to a server, 
the client typically connects to a specific port on the server and requests that the server 
respond to the client over an ephemeral, or short lived, TCP or UDP port. On Windows Server 2003 and Windows XP 
the default range of ephemeral ports used by client applications is from 1025 through 5000. 
Under certain conditions it is possible that the available ports in the default range will be exhausted.


    Start Registry Editor.

    Browse to, and then click the following key in the registry:

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters

    On the Edit menu, click New, DWORD Value, and then add the following registry value to increase the number of ephemeral ports that can by dynamically allocated to clients:

    Value name
    	

    MaxUserPort

    Value data
    	

    <Enter a decimal value between 5000 and 65534 here>
    Close Registry Editor.

    Aa560610.note(en-us,BTS.20).gifNote
    You must restart your computer for this change to take effect.

    Aa560610.note(en-us,BTS.20).gifNote
    Increasing the range of ephemeral ports used for client TCP/IP connections consumes Windows kernel memory. Do not increase the upper limit for this setting to a value higher than is required to accommodate client application socket connections so as to minimize unnecessary consumption of Windows kernel memory.

Reduce the client TCP/IP socket connection timeout value from the default value of 240 seconds


    Start Registry Editor.

    Browse to, and then click the following key in the registry:

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters

    On the Edit menu, click New, DWORD Value, and then add the following registry value to reduce the length of time that a connection stays in the TIME_WAIT state when the connection is being closed. While a connection is in the TIME_WAIT state, the socket pair cannot be reused:

    Value name
    	

    TcpTimedWaitDelay

    Value data
    	

    <Enter a decimal value between 30 and 240 here>
    Close Registry Editor.

    Aa560610.note(en-us,BTS.20).gifNote
    You must restart your computer for this change to take effect.

    Aa560610.note(en-us,BTS.20).gifNote
    The valid range of this value is 30 through 300 (decimal). The default value is 240.

Follow the recommendations in Avoiding DBNETLIB Exceptions for disabling the denial of service attack security feature that is implemented with Windows Server 2003 SP1 and later.
