---
ms.date: 2017-06-05
keywords: "powershell,командлет"
title: "Получение сведений о командах"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="c43ad-103">Получение сведений о командах</span><span class="sxs-lookup"><span data-stu-id="c43ad-103">Getting Information About Commands</span></span>
<span data-ttu-id="c43ad-104">Командлет **Get-Command** Windows PowerShell возвращает все команды, доступные в текущем сеансе.</span><span class="sxs-lookup"><span data-stu-id="c43ad-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="c43ad-105">При вводе **Get-Command** в командной строке Windows PowerShell появятся выходные данные, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="c43ad-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="c43ad-106">Эти выходные данные выглядят так же, как и выходные данные справки Cmd.exe: сводная таблица внутренних команд.</span><span class="sxs-lookup"><span data-stu-id="c43ad-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="c43ad-107">Во фрагменте выходных данных команды **Get-Command**, показанном выше, все команды имеют CommandType командлета.</span><span class="sxs-lookup"><span data-stu-id="c43ad-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="c43ad-108">Командлет является встроенным типом команды Windows PowerShell — типом, который примерно соответствует командам **dir** и **cd** Cmd.exe и встроенным командам в оболочках UNIX, например BASH.</span><span class="sxs-lookup"><span data-stu-id="c43ad-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="c43ad-109">В выходных данных команды **Get-Command** все определения закачиваются многоточием (...), указывая, что PowerShell не может отображать все содержимое в доступном пространстве.</span><span class="sxs-lookup"><span data-stu-id="c43ad-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="c43ad-110">При отображении выходных данных через Windows PowerShell служба форматирует их как текст, а затем упорядочивает таким образом, чтобы данные полностью помещались в окне.</span><span class="sxs-lookup"><span data-stu-id="c43ad-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="c43ad-111">Об этом речь пойдет далее в разделе о модулях форматирования.</span><span class="sxs-lookup"><span data-stu-id="c43ad-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="c43ad-112">Командлет **Get-Command** содержит параметр **Syntax**, который возвращает синтаксис каждого командлета.</span><span class="sxs-lookup"><span data-stu-id="c43ad-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="c43ad-113">Чтобы получить синтаксис командлета Get-Help, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c43ad-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="c43ad-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="c43ad-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="c43ad-115">Отображение доступных типов команд</span><span class="sxs-lookup"><span data-stu-id="c43ad-115">Displaying Available Command Types</span></span>
<span data-ttu-id="c43ad-116">Команда **Get-Command** не перечисляет все команды, доступные в Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c43ad-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="c43ad-117">Вместо этого команда **Get-Command** перечисляет только командлеты в текущем сеансе.</span><span class="sxs-lookup"><span data-stu-id="c43ad-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="c43ad-118">Windows PowerShell фактически поддерживает несколько других типов команд.</span><span class="sxs-lookup"><span data-stu-id="c43ad-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="c43ad-119">Псевдонимы, функции и скрипты также являются командами Windows PowerShell, хотя они не описываются подробно в руководстве пользователя Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c43ad-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="c43ad-120">Внешние файлы, исполняемые или содержащие обработчик зарегистрированных типов файлов, также классифицируются как команды.</span><span class="sxs-lookup"><span data-stu-id="c43ad-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="c43ad-121">Чтобы получить все команды в сеансе, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c43ad-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="c43ad-122">Так как этот список включает внешние файлы в пути поиска, они могут содержать тысячи элементов.</span><span class="sxs-lookup"><span data-stu-id="c43ad-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="c43ad-123">Полезнее рассмотреть сокращенный набор команд.</span><span class="sxs-lookup"><span data-stu-id="c43ad-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="c43ad-124">Чтобы получить собственные команды других типов, используйте параметр **CommandType** командлета **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="c43ad-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c43ad-125">Звездочка (\*) используется для сопоставления подстановочных знаков в аргументах командной строки Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c43ad-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="c43ad-126">Знак "\*" означает "сопоставление одного или нескольких символов".</span><span class="sxs-lookup"><span data-stu-id="c43ad-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="c43ad-127">Чтобы найти все команды, которые начинаются с буквы "a", введите **Get-Command a\&#42;**.</span><span class="sxs-lookup"><span data-stu-id="c43ad-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="c43ad-128">В отличие от сопоставления подстановочных знаков в Cmd.exe, подстановочный знак Windows PowerShell будет также сопоставлять точку.</span><span class="sxs-lookup"><span data-stu-id="c43ad-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="c43ad-129">Чтобы получить псевдонимы команд, которые являются назначенными псевдонимами команд, введите:</span><span class="sxs-lookup"><span data-stu-id="c43ad-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="c43ad-130">Чтобы получить функции текущего сеанса, введите:</span><span class="sxs-lookup"><span data-stu-id="c43ad-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="c43ad-131">Чтобы отобразить скрипты в пути поиска Windows PowerShell, введите:</span><span class="sxs-lookup"><span data-stu-id="c43ad-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```
