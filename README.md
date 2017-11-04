# About MultisortTableView

MultisortTableView is a Qt widget inherits from QTableView, which can sort table by miltiple columns.
To sort data their use AlphanumSortProxyModel inherits from QSortFilterProxyModel and sort data by alphanum algorithm (for more information about algorithm see http://www.davekoelle.com/alphanum.html).

To use MulrisortTableView in your project next files needed to be include:
AlphanumComparer.h - comparer, which use alphanum alghoritm to compare values;
AlphanumSortProxyModel.h - proxy model, that used to sort data in TableView with alphanum alghoritm;
ColumnsSorter.h - helper, which strore information about sorted columns;
MultisortTableView.h, MultisortTableView.cpp - TableView, which used ColumnsSorter class and AplhanumSortProxyModel to sort data by multiple columns.

MultisortTableView add two functions to QTableView API:
void setSortIcons( QIcon ascIcon, QIcon descIcon ) - set icons of sorting order (by default used QStyle::SP_ArrowUp and QStyle::SP_ArrowDown icons);
void setModifier ( Qt::KeyboardModifier modifier ) - set modifier to handling multicolumn sorting (by default used ControlModifier).

# How to use

How to use:
// Create a table model
QSqlTableModel *users = new QSqlTableModel;
users->setTable( "users" );
users->select( );
// Create and customize widget
MultisortTableView tableView;
tableView.setModifier( Qt::ShiftModifier );
tableView.setSortingEnabled( true );
tableView.setSortIcons( QIcon(":/icons/bullet_arrow_up.png"),
                        QIcon(":/icons/bullet_arrow_down.png") );
tableView.setSelectionBehavior( QAbstractItemView::SelectRows );
tableView.setModel( users );
tableView.show();

# demo

![](https://i.imgur.com/wuLBeNP.png)

# Test environment

Qt 5.9 By：msvc2015 32bit