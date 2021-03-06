# ABAP LEARNING RECORDS
## TIPS：
- **快捷键** :
    - Shift + F1 : 格式化
    - Ctrl + F1 : 编辑/查看切换
    - Ctrl + F2 : 编译检查
    - Ctrl + F3 : 激活
    - Ctrl + F6 : 调用function等
    - Ctrl + 「< / >」 : 批量注释/取消注释
    - Ctrl + D : 快速复制粘贴选择的某一行代码

## SOAP:
- **_SOAP:_ Simple Object Access Protocol，简单对象访问协议**
- **WebService三要素：**
    - _SOAP「Simple Object Access Protocol」，用来描述传递信息的格式；_
    - _WSDL「Web Services Description Language」，用来描述如何访问具体的接口；_
    - _UDDI「Universal Description Discovery and Integration」,用来管理、分发、查询WebService；_
- **相关定义：**
    - _SOAP封装「envelop」，它定义了一个框架，描述消息中的内容是什么，是谁发送的，谁应当接受并处理它以及如何处理它们；_
    - _SOAP编码规则「encoding rules」，它定义了一种序列化机制，用于表示应用程序需要使用的数据类型的实例；_
    - _SOAP RPC表示「RPC representation」，它定了一个协定，用于表示远程过程调用和应答；_
    - _SOAP绑定「binding」，它定义了SOAP使用哪种协议交换信息。使用HTTP/TCP/UDP协议都可以；_
    
## TECHNICAL SUMMARY：
- **创建内表时：先定义结构，按参照结构定义内表**
- **_types_ 定义的并不是结构体对象,只是结构类型,不能作为工作区。当定义的内表没有表头行「工作区」时,必须为其定义一个结构体作为工作区,否则无法使用此内表.如果没有给内表定义工作区,则在定义内表时必须声明表头行「with header line」.**
- **_TYPES与DATA区别:_ TYPES是用来定义某种类「型」的,需「用DATA语句」实例化后才可以使用；而DATA是用来定义数据对象「实例变量」的,对于用DATA直接定义的结构体对象「不参照其它结构类型」，其同时也是一个结构类型.**
- **对标准数据库表的修改，需要调用BAPI处理**
- **数据处理需要先分组，不能一行一行调用BAPI处理，因为系统存在缓存，修改单据是需要锁定后才能处理。
    Eg : 当前锁定处理第一条单据，之后没有及时解锁，第二条数据便无法处理，因而漏处理一条数据，出现bug**
- **方法调用**：
    - _当是静态方法「static method」时，使用 "class=>method" ；_
    - _当为实例方法「instance method」时，使用 "class->method"；_
***
- **代码规范**：
    - _变量命名要规范，固定使用一种。g代表全局，l代表本地，w代表工作区，t代表内表 ;_
    - _方法命名：用名词 + 动词，eg: `frm_check_data`;_
***
- **alv实现方法**
    - [ABAP ALV分类以及对应的函数，类小结](http://www.baidusap.com/abap/alv/4709 "ABAP ALV")
    
- **数据字典中的数据类型与ABAP中的中数据类型对应关系**：

数据字典预制类型|ABAP类型|运行长度|说明
---|---|---|---|
ACCP|N(6)|6|会计计算周期
CHAR|C(n)|1-255|字符
CLNT|C(3)|3|集团,数据区域代码
CUKY|C(5)|5|货币代码
CURR(n,m)|P((n+1)/2)DECIMALm|42736|货币金额
DATS|D(8)|8|日期
DEC n,m|P((n+1)/2)DECIMALm|n(1-31)m(1-17)|数值计算
FLTP|F(8)|18|浮点数
INT1|X(1)(类型b)|3|单字节整形数
INT2|X(2)|(类型s)|5|双字节整形数
INT4|X(4)|(类型i)|10|四字节整形数
LANG|C(1)|内部1位外部2位|语言代码
LCHR|C(n)|256-最大值|长字符
LRAW|X(n)|256-最大值|长位字串
NUMC n|N(n)|1-255|数值文字
PREC|X(2)|16|精确度
QUAN n,m|P((n+1)/2)DECIMALm|42736|数量
RAW n|X(n)|1-255|位字串
TIMS|T(6)|6|时间
VARC n|C(n)|255-最大值|长字符(仅3.0前可用)
STRING|STRING|1-最大值|字符串
RAWSTRING|XSTRING|1-最大值|位字符串
UNIT|C(n)|2~3|单位

