# Принцип эквивалентности повторного использования и выпуска [draft]

Оригинальный текст из книги Робертом Мартина [Agile Principles, Patterns, and Practices in C#](https://www.amazon.com/Agile-Principles-Patterns-Practices-C/dp/0131857258).

---
**Принцип эквивалентности повторного использования и выпуска (Reuse/Release Equivalence Principle – REP)**

Единица повторного использования равна единице выпуска.

---

Чего вы ожидаете от автора библиотеки классов, которую планируете повторно использовать? Разумеется, хотелось бы иметь хорошую документацию, работающий код, четко специфицированные интерфейсы и т. д. Но это еще не все.

Во-первых, чтобы повторное использование написанного этим автором кода вообще имело смысл, вы хотите иметь гарантию, что автор будет поддерживать свое детище. Ведь если поддерживать код предстоит вам, то придется потратить на его изучение массу времени, а тогда уж лучше спроектировать компонент поменьше, зато под свои конкретные нужды.

Во-вторых, вы хотите, чтобы автор извещал вас обо всех планируемых изменениях в интерфейсе и функциональности кода. Но одного извещения недостаточно. Нужно еще, чтобы автор обеспечил возможность отказаться от использования новых версий. А то, не дай бог, он выпустит новую версию как раз тогда, когда у вас трещит по швам график, или внесет изменения, несовместимые с вашей системой.

Но если вы решите отказаться от новой версии, то автор должен гарантировать поддержку старой версии в течение какого-то периода времени. Может быть, всего три месяца, может быть, год – это вопрос обсуждаемый. Но автор не может просто порвать с вами, отказав во всякой поддержке. Если автор не соглашается поддерживать старые версии, то вы всерьез задумайтесь, стоит ли использовать такой код и целиком зависеть от капризов автора.

Этот вопрос в основном политический. Он касается организационных аспектов процесса поддержки, призванного защитить интересы людей, собирающихся использовать сторонний код. Но политические и организационные вопросы оказывают глубокое влияние на способ пакетирования ПО. Для того чтобы дать гарантии, в которых нуждаются пользователи, автор организует свою программу в виде набора повторно используемых компонентов и присваивает им номера выпуска.

Таким образом, принцип REP гласит, что единица повторного использования, компонент, не может быть меньше единицы выпуска. Все, что предназначено для повторного использования, должно управляться какой-то системой учета выпусков. Не может быть так, чтобы разработчик просто написал какой-то класс и объявил его повторно используемым. О возможности повторного использования можно говорить только тогда, когда внедрена некая система учета выпусков и обеспечены гарантии извещения, надежности и поддержки, в которых так нуждаются потенциальные пользователи.

Принцип REP дает первую подсказку, как разбить дизайн на компоненты. Раз в основе повторного использования должны лежать компоненты, значит, повторно используемые компоненты должны состоять из повторно используемых классов. Поэтому по крайней мере некоторые компоненты должны содержать повторно используемые наборы классов. Тот факт, что разбиение программы определяется политическими факторами, поначалу выглядит настораживающим, но ведь ПО – не математически безупречная сущность, которую можно структурировать, руководствуясь исключительно математически строгими правилами. ПО – продукт деятельности человека, призванный служить человеческим нуждам. ПО создается людьми и для людей. И если мы собираемся его повторно использовать, то и разбивать на компоненты должны так, чтобы людям было удобно.

И какие из этого можно сделать выводы касательно внутренней структуры компонента? Рассматривать его состав следует с точки зрения потенциальных пользователей. Если компонент содержит ПО, которое допускает повторное использование, то в нем не должно быть частей, спроектированных без учета повторного использования. *Либо все классы, включенные в компонент, можно использовать повторно, либо ни один*.

Далее, сам факт повторного использования не является единственным критерием; следует еще принимать во внимание, кто будет использовать компонент. Конечно, библиотеку контейнерных классов можно использовать повторно. Как и каркас для построения финансового ПО. Но вряд ли стоит делать их частями одного и того же компонента, потому что далеко не все заинтересованные в библиотеке контейнерных классов нуждаются в финансовом каркасе. Таким образом, желательно, чтобы все классы в компоненте были ориентированы на одну и ту же аудиторию.

Плохо если потенциальные пользователи обнаружат в компоненте как необходимые, так и совершенно бесполезные для них классы.

Адаптировал: [Кротов Артём](https://fb.com/artem.v.krotov).

Остались вопросы? Задавай в [нашем чате](https://t.me/technicalexcellenceru).