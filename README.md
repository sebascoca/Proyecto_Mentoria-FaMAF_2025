# Proyecto_Mentoria-FaMAF_2025

## Predicción del tránsito en la Ciudad de Córdoba


### Descripción y objetivos del proyecto

Los mapas de ruidos son herramientan con que cuentan los municipios para planificar y monitorear el crecimiento de las ciudades. 
La construcción de estos mapas depende de la disponibilidad de datos, entre algunos de los más importantes podemos mencionar los obtenidos de las estaciones de monitoreo, simulaciones numéricas y de colaboración abiertas de la ciudadanía (crowdsourcing), entre otras.
Para las simulaciones numéricas, la principal fuente de generación de ruido se corresponde con el tránsito vehicular y factores asociados al mismo.

El objetivo de este proyecto es la construcción de un modelo predictivo, de
clasificación del tránsito y caracterización de calles de la ciudad de Córdoba,
ambos dependientes del tiempo como principal variable. El modelado se realizará
a través de modelos de Aprendizaje Supervisado/no Supervisado principalmente.

El trabajo propuesto busca relacionar y vincular el dataset con datos sobre el clima, paros de transporte, marchas, restricción vehicular por situaciones eventuales u ordenanza municipal, etc. y ver su efecto en el flujo del tránsito. 

Si bien no será parte del presente proyecto, los resultados serán de utilidad para alimentar un modelo de mapa de ruido para la Ciudad de Córdoba.

El proyecto busca responder las siguientes preguntas:

- ¿Cómo se comporta el flujo vehicular en las principales avenidas de la Ciudad
  de Córdoba?
- ¿Cómo varía el flujo vehicular durante los distintos días de la semana y
  horarios?
- ¿El flujo vehicular presenta características estacionales?
- ¿Cómo afecto la pandemia al tránsito?
- ¿Qué otros factores se pueden identificar que afecten al flujo vehicular?


En este __Proyecto de Ciencia de Datos__ se analizará el flujo vehicular en la
Ciudad de Córdoba con datos disponibles desde Agosto de 2019 a la actualidad, obtenidos de la página de la [Analítica de Tráfico de la
Municipalidad de
Córdoba](1)
correspondiente a la cámara ubicada en Av. Olmos esquina Av. Maipu.

La carpeta con los datos contiene archivos `.json` con información del flujo
vehicular. El nombre de cada archivo se especifica de la siguiente forma:

> _año_._mes_._it_.json

Donde _it_ es el _indicador de turno_, puede tomar los siguientes valores y se
corresponde con el siguiente _turno_ y _rango horario_:

 _it_ | _turno_ | _rango horario_
-------|:-:|:------:
 0 | MADRUGADA | de 0 a 6 h
 1 | MAÑANA | de 6 a 12 h
 2 | SIESTA | de 12 a 16 h
 3 | TARDE | de 16 a 21 h
 4 | NOCHE | de 21 a 24 h


Dentro de cada archivo `.json` las variables con datos, en principio relevantes,
son (tener cuidado que se presentan como listas/vectores):

	results[0] > resutl > data > dsr -> DS[0]: toda la info relevante

	  > PH[0] > DM0[#] > C: datos de vehículos para cada columna (0 hasta el valor final)
				   vector [día-1, cantidad, día de semana según cuando comienza]
					Ver el significado del resto de datos 
	  > ValueDicts 
	    > D0: fechas (vector)
	    > D1: turno (vector)
	    > D2: va la cantidad de vehículos sacada de DM0 (vector vacío) 
	    > D3: día de la semana, se corresponde con el tercer elemento de C en DM0 comenzando por el primer día en el mes (vector)
	    > D4: fecha (año/mes, vector)
	    > D5: rango horario (vector, se encuentra ordenado temporalmente)


La salida para que se vea como se presenta en la web debería ser:

    Fecha, # vehículos, turno, activo, mark, diaSemana, periodo (año/mes), IntervaloSegmento

<!--
(1): https://app.powerbi.com/view?r=eyJrIjoiMjg1YmRjODktZGRjOS00ODMxLWFiOTMtZTQzZDViZjNkMWE5IiwidCI6ImU4YjUzOTJiLWM1NmQtNGM4Ni1iNjU4LWJjYmFhNzM1ZDFjZCIsImMiOjR9
-->
